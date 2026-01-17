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

Add this plugin to your Claude Code configuration:

```bash
claude mcp add-json don-skills '{"type": "plugin", "path": "/path/to/don-skills"}'
```

Or add to your `.claude/plugins.json`:

```json
{
  "plugins": ["/path/to/don-skills"]
}
```

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

Content is sourced from developer.overheid.nl and subject to their licensing terms.
