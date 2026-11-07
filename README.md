# amp-contrib

Curated skills, tools, MCPs and commands for [Amp](https://ampcode.com).

## Installation

```bash
# Install a specific skill
amp skill add ampcode/amp-contrib/skill-name

# Install all skills from the repo
amp skill add ampcode/amp-contrib
```

## Media services by Ace Data Cloud

Independently install one service Skill. Each includes native MCP configuration, a service-specific tool allowlist, and English/Chinese API-key instructions. The service name comes first; Ace Data Cloud provides the integration and API account. These are not official plugins from the model/service makers.

| Service | Install | Guide |
| --- | --- | --- |
| Suno by Ace Data Cloud | `amp skill add ampcode/amp-contrib/suno-by-acedatacloud` | [Guide](.agents/skills/suno-by-acedatacloud/README.md) |
| Seedance by Ace Data Cloud | `amp skill add ampcode/amp-contrib/seedance-by-acedatacloud` | [Guide](.agents/skills/seedance-by-acedatacloud/README.md) |
| HappyHorse by Ace Data Cloud | `amp skill add ampcode/amp-contrib/happyhorse-by-acedatacloud` | [Guide](.agents/skills/happyhorse-by-acedatacloud/README.md) |
| GPT Image by Ace Data Cloud | `amp skill add ampcode/amp-contrib/gpt-image-by-acedatacloud` | [Guide](.agents/skills/gpt-image-by-acedatacloud/README.md) |
| Nano Banana by Ace Data Cloud | `amp skill add ampcode/amp-contrib/nano-banana-by-acedatacloud` | [Guide](.agents/skills/nano-banana-by-acedatacloud/README.md) |

An existing Amp account and a private `ACEDATACLOUD_API_TOKEN` are required. Generation uses your Ace balance; Amp inference may have its own cost. A returned task ID is not completion: poll the same ID and require a successful terminal result. Do not run a paid generation as an installation test. See the individual guide for restrictions and troubleshooting.

## License

MIT
