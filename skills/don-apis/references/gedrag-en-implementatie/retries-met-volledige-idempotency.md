# Veilige retries met volledige idempotency

Bij een schrijfoperatie kan het voor een client onduidelijk zijn of deze is
geslaagd, bijvoorbeeld door een netwerkfout. In dat geval zal de client de
operatie opnieuw proberen. Een ongewenst effect is dat er door het opnieuw
proberen meer wijzigingen worden doorgevoerd dan de bedoeling was. Om dit te
voorkomen is het van belang dat alle API-operaties die data wijzigen volledig
[_idempotent_](https://en.wikipedia.org/wiki/Idempotence) zijn.

Een operatie is _idempotent_ als het herhalen ervan geen extra effect heeft op
de toestand van de server. `GET`, `PUT` en `DELETE` zijn volgens de
HTTP-specificatie idempotent. Een herhaalde `DELETE /items/2` zal bijvoorbeeld
de tweede keer een `404` geven, maar de toestand van de server blijft
consistent. `POST` en `PATCH` zijn dit van nature niet: een herhaalde
`POST /items` zou een duplicaat item aanmaken. Voor deze operaties kan
idempotent gedrag worden afgedwongen door een `Idempotency-Key` header toe te
voegen.

| HTTP Verb | Idempotency mechanisme                                                                       |
| --------- | -------------------------------------------------------------------------------------------- |
| GET       | Safe request [RFC 9110](https://datatracker.ietf.org/doc/html/rfc9110#name-safe-methods)     |
| PUT       | Idempotent [RFC 9110](https://datatracker.ietf.org/doc/html/rfc9110#name-idempotent-methods) |
| DELETE    | Idempotent [RFC 9110](https://datatracker.ietf.org/doc/html/rfc9110#name-idempotent-methods) |
| POST      | Header: `Idempotency-Key`                                                                    |
| PATCH     | Header: `Idempotency-Key`                                                                    |

## Werking

1.  De client genereert een unieke `Idempotency-Key` (bijvoorbeeld een UUID)
    voor een uit te voeren operatie.
2.  De client verstuurt de `POST` of `PATCH` request met deze key in de header.
3.  De server controleert of deze `Idempotency-Key` al eerder is ontvangen.
    - **Bestaande key**: De server verwerkt de operatie niet opnieuw, maar
      stuurt direct de eerder opgeslagen response terug.
    - **Nieuwe key**: De server verwerkt de operatie en slaat de response
      (statuscode en body) op, gekoppeld aan de `Idempotency-Key`.
4.  Als de client een retry moet uitvoeren (bijvoorbeeld door een netwerkfout),
    moet exact dezelfde `Idempotency-Key` worden gebruikt.

## Transactionele veiligheid

Voor kritieke operaties is het aan te bevelen voor de client om de
`Idempotency-Key` lokaal en duurzaam op te slaan _voordat_ de request wordt
verstuurd. Stel dat een client crasht nadat het de request heeft verstuurd, maar
voordat het een response heeft ontvangen. Bij het herstarten weet de client niet
of de operatie op de server is geslaagd. Door de `Idempotency-Key` vooraf op te
slaan, kan de client na een herstart de request veilig opnieuw proberen met
dezelfde key. De server zal dan ofwel de operatie alsnog uitvoeren (als de
eerste poging nooit aankwam), of de opgeslagen response retourneren (als de
eerste poging wel slaagde).

Een correcte implementatie van idempotency op de server vereist transactionele
veiligheid. Het verwerken van de business-operatie en het opslaan van de
`Idempotency-Key` met de bijbehorende response moeten binnen dezelfde atomaire
transactie plaatsvinden. Zonder deze garantie kan een race condition optreden,
waarbij een operatie onterecht twee keer wordt uitgevoerd.

## Levensduur van de key

De server bewaart de `Idempotency-Key` en de bijbehorende response voor een
bepaalde tijd om de garantie te kunnen bieden. De bewaartermijn is afhankelijk
van het verwachte retry-patroon van clients, waarbij 24 uur een gangbare keuze
is. De gekozen termijn moet door de API-provider worden gedocumenteerd. Na het
verlopen van de termijn behandelt de server een request met dezelfde key als een
nieuwe operatie.

## Voorbeeld in OpenAPI

```yaml
paths:
  /items:
    post:
      summary: Maak een nieuw item aan
      parameters:
        - name: Idempotency-Key
          in: header
          required: true
          description:
            Een unieke sleutel om de idempotent-garantie te bieden. De server
            bewaart deze sleutel 24 uur.
          schema:
            type: string
            format: uuid
      requestBody:
        content:
          application/json:
            schema:
              $ref: "#/components/schemas/Item"
      responses:
        "201":
          description: Item aangemaakt
```