---
name: searching-amp-docs
description: Searches current official Amp documentation and gives source-backed explanations of Amp features, setup, CLI usage, modes, threads, projects, orbs, runners, tools, skills, MCP, plugins, SDKs, configuration, security, pricing, and troubleshooting. Use whenever a user asks how Amp works, what Amp supports, how Amp features compare, whether behavior is current or documented, or how to accomplish something with Amp—even if they do not explicitly ask to search the docs.
---

# Searching Amp Docs

Answer questions about Amp from current, official documentation. Optimize explanations for users who may not know Amp terminology yet.

## Documentation Sources

Use these sources for different purposes:

- [Amp's official `llms.txt`](https://ampcode.com/llms.txt) is the machine-readable documentation entrypoint. It currently links only to the manual and SDK.
- [The Amp manual](https://ampcode.com/manual) is the primary source for product behavior and workflows.
- Specialized official pages listed in [references/docs-index.md](references/docs-index.md) are authoritative for their exact contracts, such as SDK and Plugin API details.
- Other official `ampcode.com` pages may cover current models, pricing, security, service status, account settings, or release announcements.

The bundled index expands `llms.txt` for topic discovery, but it is not an authoritative or frozen copy of the documentation. Amp changes quickly. Read the relevant live page before answering factual questions; do not answer from either index or model memory alone.

## Workflow

1. Identify the user's actual goal and likely topic. Translate informal terms when necessary—for example, “cloud machine” likely means an orb and “rules file” likely means `AGENTS.md`.
2. Read `references/docs-index.md` only as much as needed to choose the best official page and section.
3. Fetch the selected page with `read_web_page`:
   - Give it a specific objective containing the user's question and relevant terminology.
   - Use `fullContent: true` when auditing a contract, comparing options, extracting every field, or checking whether a feature is documented.
   - Use `forceRefetch: true` for “latest/current” questions and volatile information such as models, modes, pricing, limits, settings, or supported platforms.
4. If the index is missing the topic or a link is stale, check the live [`llms.txt`](https://ampcode.com/llms.txt), then use `web_search` with `site:ampcode.com` queries and read the most relevant official result. Do not substitute blogs or third-party tutorials when official documentation exists.
5. Read enough surrounding context to determine scope, prerequisites, defaults, and whether guidance is current. Search results and isolated excerpts can omit qualifiers.
6. If official pages conflict, prefer the more specific current reference over summaries, report the conflict, and avoid silently combining incompatible guidance. Use release history or source code only when the official docs are incomplete, and label that evidence separately.
7. Answer the goal directly. Include:
   - a plain-language explanation;
   - exact commands, settings, file locations, or code when useful;
   - prerequisites, scope, defaults, and important caveats;
   - links to the specific official pages used.
8. If the official docs do not answer the question, say so clearly. Separate documented behavior from any reasonable inference and suggest the narrowest next step, such as `amp --help`, `amp tools list`, `amp config keymap`, the service-status page, or Amp support.

## New-User Guidance

- Define Amp-specific terms on first use: thread, mode, project, orb, runner, skill, plugin, MCP server, Oracle, Librarian, and Painter.
- Prefer a short recommended path before listing alternatives.
- Explain where to run commands and whether a file is user-wide, workspace-specific, or committed to a repository.
- When several features overlap, compare them explicitly. Common distinctions include:
  - local CLI vs orb vs runner;
  - `AGENTS.md` vs skill vs plugin vs MCP;
  - main agent vs subagent vs Oracle vs Librarian;
  - thread visibility vs project membership;
  - CLI execute mode vs SDK;
  - `.agents/setup` vs `.agents/resume` vs `.amp/services.yaml`.
- Preserve the user's operating system and interface context. Do not give macOS-only clipboard or path instructions to a Windows/WSL user.
- Never invent a command, flag, setting, API field, keybinding, model assignment, price, or limit. Verify exact syntax in the live docs.

## Answer Patterns

### “How do I …?”

Give the shortest working sequence first, then explain what each step does and mention only relevant alternatives.

### “What is …?”

Give a one-sentence definition, when to use it, one concrete example, and the official reference.

### Comparison or Architecture Question

Use a compact table when it improves clarity. Compare purpose, where it runs, persistence/scope, cost or security implications when documented, and the recommended use case.

### Troubleshooting

1. Confirm the platform, interface, and exact failure.
2. Check documented prerequisites and diagnostics.
3. Provide safe diagnostic commands before suggesting configuration changes.
4. For outages, check [Amp service status](https://ampcodestatus.com).
5. For unresolved client issues, explain how to generate a diagnostic report and contact support without exposing secrets.

### “Show me every Amp feature”

Do not paste the whole manual. Use the feature map in `references/docs-index.md` to provide a structured learning path, then offer to walk through one area with live documentation. A useful progression is:

1. installation, interfaces, modes, and prompting;
2. threads, file mentions, images, and `AGENTS.md`;
3. projects, orbs, runners, and remote control;
4. built-in tools, skills, subagents, Oracle, Librarian, and Painter;
5. review checks, MCP, plugins, and permissions;
6. CLI automation, configuration, and SDKs;
7. pricing, enterprise controls, security, and troubleshooting.

## Citation Rules

- Link claims to the most specific official page available.
- For the large main manual, use the section anchor from the index when possible.
- Cite specialized references for exact SDK or plugin API contracts.
- Do not imply that this skill's bundled index is maintained by Amp or replaces the official manual.
