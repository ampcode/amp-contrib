# Amp Official Documentation Index

This is an expanded routing index for Amp's documentation. It complements the sparse public `llms.txt`; the linked live pages remain authoritative.

## Start Here

- [Owner's Manual](https://ampcode.com/manual) — primary guide to installing, using, extending, configuring, and paying for Amp
- [Installation](https://ampcode.com/install) — account-specific installation and editor integration instructions
- [Modes and models](https://ampcode.com/modes) — current mode-to-model assignments
- [Pricing](https://ampcode.com/pricing) — current plan and usage pricing
- [Service status](https://ampcodestatus.com) — incidents and uptime
- [Support](https://ampcode.com/support) — official help channels

## Owner's Manual Feature Map

### Fundamentals

- [Why Amp](https://ampcode.com/manual#why-amp) — product philosophy: multi-model, opinionated, frontier, and thread-based
- [Get started](https://ampcode.com/manual#get-started) — sign-in, CLI installation, updates, and initial setup
- [IDE integrations](https://ampcode.com/manual#ide) — VS Code-family editors, JetBrains, Neovim, Zed, and `ide connect`
- [Agent modes](https://ampcode.com/manual#agent-modes) — low, medium, high, and ultra
- [How to prompt](https://ampcode.com/manual#how-to-prompt) — task scoping, explicit context, planning-only requests, and verification guidance

### Context and Interaction

- [`AGENTS.md`](https://ampcode.com/manual#AGENTS.md) — project, subtree, personal, and organization guidance; fallback filenames
- [Granular guidance](https://ampcode.com/manual#AGENTS.md) — file mentions, globbed references, and scoped frontmatter rules
- [Referencing threads](https://ampcode.com/manual#referencing-threads) — reuse another thread by URL, ID, or `@@` search
- [Finding threads](https://ampcode.com/manual#finding-threads) — keyword and filter-based thread search
- [Archiving threads](https://ampcode.com/manual#archiving) — remove threads from the active list while retaining access
- [Attaching images](https://ampcode.com/manual#images) — clipboard and file-path image inputs
- [Mentioning files](https://ampcode.com/manual#mentioning-files) — add workspace files with `@`
- [Message editing and queueing](https://ampcode.com/manual#usage) — edit, queue, steer, or interrupt messages

### Projects and Remote Execution

- [Projects](https://ampcode.com/manual#projects) — repository, settings, secrets, and related threads
- [Repository](https://ampcode.com/manual#repository) — GitHub, Git URL, or Amp-hosted repositories
- [Changes workflow](https://ampcode.com/manual#changes-workflow) — ship directly or push a branch/PR
- [Orbs overview](https://ampcode.com/manual#orbs) — remote machines for unsupervised agent work
- [Full Orbs manual](https://ampcode.com/manual/orbs) — sizes, billing, terminal, sync, setup, secrets, services, and portals
- [Runners](https://ampcode.com/manual#runners) — let ampcode.com start threads on a live machine running Amp
- [Thread sharing](https://ampcode.com/manual#thread-sharing) — unlisted, workspace, group, and private visibility
- [Remote control](https://ampcode.com/manual#remote-control) — continue a running CLI thread from the web

### Tools and Agent Capabilities

- [Tools](https://ampcode.com/manual#tools) — built-in tools, trust model, and `amp tools list`
- [Agent skills](https://ampcode.com/manual#agent-skills) — task-specific instructions/resources and installation locations
- [Subagents](https://ampcode.com/manual#subagents) — isolated delegated work for complex or parallel tasks
- [Oracle](https://ampcode.com/manual#oracle) — frontier-model second opinion for hard reasoning, debugging, and review
- [Librarian](https://ampcode.com/manual#librarian) — deep search and explanation of public or connected private GitHub repositories
- [Painter](https://ampcode.com/manual#painter) — image generation and editing
- [Code review](https://ampcode.com/manual#code-review) — `amp review`, review requests, and custom checks

### Extending Amp

- [MCP](https://ampcode.com/manual#mcp) — local and remote Model Context Protocol servers
- [MCP OAuth](https://ampcode.com/manual#mcp-oauth) — automatic and manual OAuth for remote servers
- [Workspace MCP trust](https://ampcode.com/manual#mcp) — approval of workspace-defined servers
- [MCP best practices](https://ampcode.com/manual#mcp) — skill bundling, focused tool sets, and loading precedence
- [Permissions](https://ampcode.com/manual#permissions) — default tool behavior and plugin-based policy controls
- [Plugins](https://ampcode.com/manual#plugins) — TypeScript extensions for events, tools, commands, UI, and AI classification
- [Plugin locations](https://ampcode.com/manual#plugin-locations) — project, system, and workspace-global scopes
- [Writing plugins](https://ampcode.com/manual#writing-plugins) — lifecycle, reload, and plugin structure
- [Plugin events](https://ampcode.com/manual#event-examples) — `session.start`, `agent.start/end`, `tool.call/result`
- [Plugin commands, tools, UI, and agents](https://ampcode.com/manual#command-tool-and-ui-examples) — registration and custom agent examples
- [Plugin API reference](https://ampcode.com/manual/plugin-api) — end-to-end example and generated `@ampcode/plugin` types

### CLI and Automation

- [CLI](https://ampcode.com/manual#cli) — interactive mode, piped input, execute mode, and flags
- [Keybindings](https://ampcode.com/manual#cli-keymap) — command palette, shortcuts, and `amp.keymap`
- [Non-interactive environments](https://ampcode.com/manual#cli-non-interactive-environments) — API-key authentication for scripts and CI
- [CLI–IDE integration](https://ampcode.com/manual#cli-editor-integration) — editor context and undo-aware edits
- [Writing prompts in the CLI](https://ampcode.com/manual#cli-writing-prompts) — newlines, `$EDITOR`, and terminal behavior
- [Streaming JSON](https://ampcode.com/manual#cli-streaming-json) — structured output and streaming input flags
- [Stream JSON schema and examples](https://ampcode.com/manual/appendix#stream-json-output) — message types, subagents, images, and Claude Code compatibility

### Configuration, Accounts, and Operations

- [Configuration](https://ampcode.com/manual#configuration) — user/workspace settings locations and precedence
- [Settings reference](https://ampcode.com/manual#core-settings) — supported `amp.*` settings, types, and defaults
- [Enterprise managed settings](https://ampcode.com/manual#enterprise-managed-policy-settings) — organization-enforced machine policies
- [Proxies and certificates](https://ampcode.com/manual#configuration) — `HTTP_PROXY`, `HTTPS_PROXY`, and custom CA certificates
- [Pricing](https://ampcode.com/manual#pricing) — usage billing, credits, and subscription guidance
- [Enterprise](https://ampcode.com/manual#enterprise) — SSO, ZDR, controls, APIs, groups, retention, and regional providers
- [Support and platforms](https://ampcode.com/manual#support) — help channels and supported operating systems/editors

## Orbs Manual Map

- [What are orbs](https://ampcode.com/manual/orbs) — fresh per-thread remote machines and project configuration
- [Orb pricing and sizes](https://ampcode.com/manual/orbs) — CPU, memory, disk, billing, pause behavior
- [Starting orb threads](https://ampcode.com/manual/orbs) — web, `amp -ox`, TUI, and plugin APIs
- [Review, terminal, and `amp sync`](https://ampcode.com/manual/orbs) — inspect remote work and mirror it locally
- [Secrets and environment variables](https://ampcode.com/manual/orbs) — project runtime configuration
- [OIDC workload identity](https://ampcode.com/manual/orbs) — short-lived identity tokens for external services
- [Orb environment](https://ampcode.com/manual/orbs) — OS and preinstalled development tools
- [Setup files](https://ampcode.com/manual/orbs) — `.agents/setup`, `.agents/resume`, `.amp/services.yaml`, and portal manifests
- [Portals](https://ampcode.com/manual/orbs) — authenticated access to development servers in an orb

## SDK Documentation

- [SDK overview and guide](https://ampcode.com/manual/sdk) — streaming, conversations, thread continuity, configuration, MCP, and skills
- [TypeScript reference](https://ampcode.com/manual/sdk/typescript) — complete TypeScript functions, types, inputs, and messages
- [Python reference](https://ampcode.com/manual/sdk/python) — complete Python functions, types, inputs, and messages
- [Access tokens](https://ampcode.com/settings/security#access-token) — SDK and non-interactive authentication

SDK guide topics include installation, `execute()`, message streaming, result extraction, working directory, logging, modes, reasoning effort, labels, visibility, permissions, cancellation, MCP, multi-turn input, settings files, and custom skills.

## Appendix and Specialized References

- [Appendix](https://ampcode.com/manual/appendix) — diagnostics, tmux, service status, enterprise controls, and Stream JSON
- [Generate a diagnostic report](https://ampcode.com/manual/appendix#report) — CLI/web reports and support workflow
- [Amp CLI in tmux](https://ampcode.com/manual/appendix#amp-cli-tmux) — extended keys and multiline input
- [MCP registry allowlist](https://ampcode.com/manual/appendix#mcp-registry-allowlist) — enterprise registry enforcement
- [Workspace thread visibility controls](https://ampcode.com/manual/appendix#workspace-thread-visibility-controls) — sharing restrictions and private defaults
- [Workspace entitlements](https://ampcode.com/manual/appendix#workspace-entitlements) — enterprise quotas and assignment precedence
- [Legacy permissions rules](https://ampcode.com/manual/appendix/legacy-permissions-rules.txt) — old settings compatibility; prefer current plugin policies for new work
- [Security reference](https://ampcode.com/security) — architecture, providers, retention, prompt injection defenses, audit logging, and disclosures
- [Workspace OpenAPI schema](https://ampcode.com/api/v2/openapi.json) — enterprise analytics and data-management API contract

## Topic Synonyms for Search

Use these mappings when a user's language differs from the manual:

| User wording | Search/documentation topic |
| --- | --- |
| cloud VM, sandbox, remote machine | orb |
| local remote worker, self-hosted worker | runner |
| conversation, session, chat | thread |
| rules, instructions, memory | `AGENTS.md`, granular guidance |
| reusable prompt, workflow package | agent skill |
| extension, hook, custom command | plugin |
| external tools, tool server | MCP |
| second opinion, deep review | Oracle |
| search GitHub or dependency source | Librarian |
| generate/edit an image | Painter |
| headless, CI, scripting | execute mode, Stream JSON, or SDK |
| preview localhost remotely | orb portal |
| startup script, install dependencies | `.agents/setup` |
| restart server after orb wakes | `.agents/resume`, services |
