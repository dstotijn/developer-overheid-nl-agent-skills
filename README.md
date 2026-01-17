# Developer.overheid.nl - Knowledge Base Skills

Agent skills for the Dutch Government Developer Portal (developer.overheid.nl) knowledge base.

## Skills

| Skill                | Description                                                       |
| -------------------- | ----------------------------------------------------------------- |
| don-apis             | API design rules, OpenAPI specs, and architecture guidelines      |
| don-leidraad         | NeRDS software development guidelines                             |
| don-security         | Security standards and authentication (DigiD, eHerkenning, OAuth) |
| don-open-source      | Open source standards and publiccode.yml                          |
| don-infra            | Infrastructure standards (Haven, FSC)                             |
| don-data             | Data standards and linked data                                    |
| don-front-end        | Front-end standards and NL Design System                          |
| don-programmeertalen | Programming language guidelines                                   |

## Installation

### Claude Code

First, install the [claude-marketplace](https://github.com/dstotijn/claude-marketplace) plugin:

```
/plugin marketplace add dstotijn/claude-marketplace
```

Then install this plugin via the `/plugin` command:

```
/plugin install developer-overheid-nl-agent-skills@dstotijn/claude-marketplace
```

### Other

This repository adheres to the [Agent Skills](https://agentskills.io/) specification. Refer to your IDE or coding agent documentation to learn how to install and use agent skills.

## Usage

Sample prompts that trigger the skills:

| Prompt | Skill |
| ------ | ----- |
| "How do I implement the Dutch API design rules?" | don-apis |
| "Create an OpenAPI spec following government standards" | don-apis |
| "What are the NeRDS guidelines for CI/CD?" | don-leidraad |
| "How do I integrate DigiD authentication?" | don-security |
| "What's the difference between OAuth and OIDC?" | don-security |
| "How do I set up a publiccode.yml file?" | don-open-source |
| "What license should I use for government open source?" | don-open-source |
| "How do I deploy to Haven?" | don-infra |
| "What is FSC (Federated Service Connectivity)?" | don-infra |
| "How do I implement the Logboek Dataverwerkingen standard?" | don-data |
| "How do I use NL Design System components?" | don-front-end |
| "What are the WCAG accessibility requirements?" | don-front-end |

## Syncing

Skills are synced from the [developer-overheid-nl/don-site](https://github.com/developer-overheid-nl/don-site) repository.

To update all skills:

```bash
python scripts/sync.py
```

To update a specific topic:

```bash
python scripts/sync.py --topic apis
```

Available topics: `apis`, `leidraad`, `security`, `open-source`, `infra`, `data`, `front-end`, `programmeertalen`

## Development

```bash
# Install dependencies
uv sync

# Validate all skills
for skill in skills/don-*/; do uv run skills-ref validate "$skill"; done
```

## License

[EUPL-1.2](LICENSE) - Content is sourced from [developer.overheid.nl](https://developer.overheid.nl).
