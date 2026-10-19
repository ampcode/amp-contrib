# Nano Banana by Ace Data Cloud for Amp

An independently installable **Nano Banana** Skill with native MCP tools, supplied by Ace Data Cloud. Search terms: Nano Banana, nano-banana, image. This does not add a default LLM provider, and it is not endorsed by Nano Banana's maker or Amp.

[简体中文](README.zh-CN.md) · [Current API pricing](https://platform.acedata.cloud/models?utm_source=amp&utm_medium=integration&utm_campaign=evergreen&utm_content=nano-banana_amp_pricing) · [Source](https://github.com/AceDataCloud/Skills/tree/main/platforms/amp/skills/nano-banana-by-acedatacloud)

## 1. Install just this service

Amp's [official Skill mechanism](https://ampcode.com/docs/customize/skills) installs a Skill and its sibling `mcp.json`. Install Amp following its [official CLI guide](https://ampcode.com/docs/cli), then sign in with your existing Amp account using `amp login`.

```bash
amp skill add AceDataCloud/Skills/platforms/amp/skills/nano-banana-by-acedatacloud
```

The source command above is published from [Ace Skills main](https://github.com/AceDataCloud/Skills/commit/6169154675fd6523ad4230c257c7f70227a7c41b) (2026-10-19). Signed-in Amp installation is still awaiting verification. The proposed official [amp-contrib directory](https://github.com/ampcode/amp-contrib) entry is pending review; **do not treat this source install as an accepted official listing**. If accepted, its independent command is `amp skill add ampcode/amp-contrib/nano-banana-by-acedatacloud`. Do not install both copies.

For a reviewed local checkout: `amp skill add ./platforms/amp/skills/nano-banana-by-acedatacloud --target /absolute/path/to/project/.agents/skills`. Amp currently requires an account even for this installer. A local copy/format check is not a signed-in Amp execution test.

## 2. Register/sign in to Ace and get your own key

1. Open [Ace Data Cloud → Applications](https://platform.acedata.cloud/console/applications?utm_source=amp&utm_medium=integration&utm_campaign=evergreen&utm_content=nano-banana_amp_api_key), register if needed, then sign in. Open **General application**; choose **Initialize General Application** if none exists.
2. Check Nano Banana service access, your balance and [current pricing](https://platform.acedata.cloud/models?utm_source=amp&utm_medium=integration&utm_campaign=evergreen&utm_content=nano-banana_amp_pricing). Copy the API key, or choose **Manage Keys → Create** for a dedicated `Amp Nano Banana` key.
3. Review expiration, usage limits and **Allowed APIs**. If restricted, allow the generation/edit and task-query routes you actually need: `/nano-banana/images, /nano-banana/tasks`. Service availability and any trial allowance are whatever your account currently shows.
4. Copy only the token value, without quotes, spaces or `Bearer `. A `platform-...` management token cannot replace a service API key.

![Ace Applications: copy a redacted key or open Manage Keys](https://raw.githubusercontent.com/AceDataCloud/SunoDify/8d3d03570e73324220f111f7fe343da0792a8071/_assets/tutorial/get-api-key-en.png)

![Ace Applications: create a dedicated API key](https://raw.githubusercontent.com/AceDataCloud/SunoDify/8d3d03570e73324220f111f7fe343da0792a8071/_assets/tutorial/create-api-key-en.png)

These are real, redacted Ace console screenshots reused from the Dify guide at source revision `8d3d035`; checked 2026-10-18. The screenshot's example key name is not an Amp setting.

## 3. Put the key in Amp's process environment

Set `ACEDATACLOUD_API_TOKEN` privately in the terminal that starts Amp. On macOS/Linux:

```bash
# Replace this placeholder locally; never paste a real key in a prompt or commit it.
export ACEDATACLOUD_API_TOKEN='YOUR_API_TOKEN'
amp
```

On PowerShell use `$env:ACEDATACLOUD_API_TOKEN = 'YOUR_API_TOKEN'` before starting Amp. The manifest contains only `Bearer ${ACEDATACLOUD_API_TOKEN}`, not your key. A new terminal needs the variable too. Hosted personal/workspace Skills run elsewhere: configure their secret in that execution environment; your local shell variable is not automatically copied.

## 4. Find and load the service

Run `amp skill list --json`, or open the Amp command palette with **Ctrl+O → skills: list**. Find `nano-banana-by-acedatacloud`, then ask Amp to load it. Skill MCP tools stay hidden until the Skill loads. `amp mcp doctor nano-banana-ace` checks the connection; `amp tools list --json` inspects active tools. Project-configured MCP servers may need `amp mcp approve nano-banana-ace` after you review their configuration; do not add a duplicate direct MCP configuration just to approve a Skill.

![Official Amp CLI command palette, unmodified reference](https://static.ampcode.com/docs/cli-command-palette.png)

Official reference from [Amp keybindings](https://ampcode.com/docs/cli/keybindings), downloaded 2026-10-18; capture date/version not published. It is **not an Ace run** and does not show the Skill selected. `page logs` is debugging, not the tool entry. Real Nano Banana installation/load/result screenshots remain pending an authorized Amp session.

For a no-generation check, ask:

> Inspect the Nano Banana by Ace Data Cloud Skill and discovered tools. Do not generate or edit media and do not call a task lookup without my existing task ID.

Inspect the discovered input schema and configuration only. This Skill has no free model-list tool; do not generate an image as an installation test. Amp inference may itself cost usage: do not run an agent turn unless it is covered by your authorized budget/subscription. Command help, file validation and tool discovery do not prove a paid result.

## 5. First requested result, then the same task

When you decide to pay for generation, ask:

> Use Nano Banana by Ace Data Cloud to create one image result. First show the current model/parameters and price for my approval. After I approve, submit once with nanobanana_generate_image, save its task ID, and query only that ID with nanobanana_get_task. Do not retry generation while waiting.

Require an explicit terminal success (`state=complete` with success, or the returned finished timestamp and successful response). Failure is terminal too. A pending task or an early media URL is not completion. Return the actual task ID and final media links. Continue `nanobanana_get_task` with its original ID after a timeout; do not rerun the entire generation workflow. Compare the corresponding usage record in Ace with that single request. Credits are not USD; conversion uses your current package price/amount.

## Troubleshooting

| Symptom | Action |
| --- | --- |
| No Skill/tools | Check installation path and `nano-banana-by-acedatacloud`, reload Skills, load this Skill, and check for an older Skill masking the same name. |
| Login prompt before install/doctor | Use the existing Amp account; the Ace API key is a separate credential. |
| 401/403 | Check the full copied service key, Nano Banana access, expiry, limits, Allowed APIs and balance; never expose the key. |
| 429 | Wait and reduce concurrency; no automatic paid retries. |
| Pending task or early URL | Query the same task ID; do not generate again. |
| 400, moderation, failed/uncertain request | Preserve the error, inspect the original task, and ask before changing parameters/model or retrying. |
| Different tools unexpectedly visible | A direct MCP setting can override the Skill server. Review existing settings; do not overwrite unrelated connections. |

## Privacy and support

The free Skill connects to `https://nanobanana.mcp.acedata.cloud/mcp`; your chosen inputs and Bearer credential are handled by Ace Data Cloud. API generation uses your Ace account and follows current prices. Review the installed files before sharing them with a workspace; never put a real key in a repository. [MCP implementation](https://github.com/AceDataCloud/NanoBananaMCP) · [Support](https://github.com/AceDataCloud/Skills/issues).
