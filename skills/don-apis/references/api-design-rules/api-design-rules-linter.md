# ADR Linter

De ADR Linter controleert of een OpenAPI Specificatie compliant is met de API
Design Rules. De linter is gebaseerd op het Open Source project
[Spectral](https://github.com/stoplightio/spectral).

## Browser

Een OpenAPI Specificatie kan online getest worden via onze online OAS Checker:
[https://developer-overheid-nl.github.io/oas-checker](https://developer-overheid-nl.github.io/oas-checker)

## CLI

Nadat je Spectral geïnstalleerd hebt, kun je een OAS via de commandline op de
volgende manier valideren:

```bash
$ npm install -g @stoplight/spectral-cli
$ spectral lint -r https://static.developer.overheid.nl/adr/ruleset.yaml $OAS_URL_OR_FILE
```

## IDE

Sommige IDEs ondersteunen Spectral via extensies of plugins. Eén daarvan is
VSCode. Hieronder staat beschreven hoe je de ADR Linter kunt gebruiken met
[de officiele Spectral extensie voor Visual Studio Code](https://github.com/stoplightio/vscode-spectral):

```bash
# Install the extension from the vscode marketplace
$ code --install-extension stoplight.spectral

# Download the ruleset to your project home
$ curl -L https://static.developer.overheid.nl/adr/ruleset.yaml > .spectral.yml

# Run the IDE
$ code
```

## Docker

```bash
$ docker run --rm --entrypoint=sh \
    -v $(pwd)/api:/locale stoplight/spectral:5.9.1 \
    -c "spectral lint -r https://static.developer.overheid.nl/adr/ruleset.yaml $OAS_URL_OR_FILE"
```

## GitLab

```yaml
spectral-lint:
  image: node:20
  stage: spectral_lint
  script:
    - npm install -g @stoplight/spectral-cli
    - curl -L https://static.developer.overheid.nl/adr/ruleset.yaml >
      .spectral.yml
    - spectral lint -r .spectral.yml $OAS_URL_OR_FILE
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'
      when: always
    - when: manual
```