# Veilige gelijktijdigheid met optimistic locking

Het kan voorkomen dat er verschillende clients gelijktijdig dezelfde bestaande
resource proberen aan te passen door middel van een `PUT`, `DELETE` of `PATCH`
operatie. Dit staat bekend als het
[_Lost Update_](https://www.w3.org/1999/04/Editing/) probleem.

Om dit probleem te voorkomen kan een API het gebruik van _Optimistic Locking_
voorschrijven. In de API specificatie kan dit worden geimplementeerd door middel
van het toevoegen van
[`ETag`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/ETag)
en
[`If-Match`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/If-Match)
headers aan onderstaande operaties.

| HTTP Verb | Concurrency control mechanisme |
| --------- | ------------------------------ |
| GET       | Header: `ETag`                 |
| PUT       | Header: `If-Match`             |
| DELETE    | Header: `If-Match`             |
| POST      |                                |
| PATCH     | Header: `If-Match`             |

## Werking

1.  Elke `GET`-respons voor een resource bevat een `ETag`-header. Deze header
    fungeert als een unieke vingerafdruk voor de specifieke versie van de
    opgevraagde data.
2.  Voor elke `PUT`-, `PATCH`- of `DELETE`-actie moet de client de `ETag`-header
    van de laatste GET-respons meesturen in de `If-Match`-header van het
    request.
3.  De server controleert of de `If-Match`-header overeenkomt met de huidige
    `ETag` van de resource.
    - Overeenkomst: de actie wordt uitgevoerd.
    - Niet overeenkomst: de actie wordt geweigerd met een
      `412 Precondition Failed` statuscode.

## Voorbeeld in OpenAPI

Hieronder een voorbeeld van hoe je dit in een OpenAPI specificatie kunt
vastleggen.

```yaml
paths:
  /items/{itemId}:
    get:
      summary: Vraag een item op
      parameters:
        - name: itemId
          in: path
          required: true
          schema:
            type: string
      responses:
        "200":
          description: OK
          headers:
            ETag:
              description: De ETag van het item.
              schema:
                type: string
    put:
      summary: Werk een item bij
      parameters:
        - name: itemId
          in: path
          required: true
          schema:
            type: string
        - name: If-Match
          in: header
          required: true
          description: De ETag van het item dat bijgewerkt moet worden.
          schema:
            type: string
      responses:
        "200":
          description: Item bijgewerkt
        "412":
          description:
            Precondition Failed. De ETag in de If-Match header komt niet overeen
            met de huidige ETag van de resource.
```