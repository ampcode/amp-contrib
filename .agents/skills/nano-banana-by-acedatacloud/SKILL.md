---
name: nano-banana-by-acedatacloud
description: Generate or edit Nano Banana images through Ace Data Cloud, then retrieve the completed image from the same task. Use for Nano Banana requests, not GPT Image or chat.
license: Apache-2.0
metadata:
  author: Ace Data Cloud
  version: "1.0.0"
  category: image
---

# Nano Banana by Ace Data Cloud

Generate or edit Nano Banana images through Ace Data Cloud, then retrieve the completed image from the same task. Use for Nano Banana requests, not GPT Image or chat.
This is an Ace Data Cloud integration, not an official Nano Banana or Amp plugin endorsement.

## Setup and tool scope

Requires Amp native Skill MCP support, an existing Amp login, and `ACEDATACLOUD_API_TOKEN` in the environment that starts Amp.

Read [README.md](README.md) for installation, illustrated API-key setup, and troubleshooting.
The sibling `mcp.json` connects only `nano-banana-ace` at `https://nanobanana.mcp.acedata.cloud/mcp` and limits tools to this service.
Reuse an existing matching connection; do not add a second server or alter unrelated settings.
Keep the API key in `ACEDATACLOUD_API_TOKEN`; never request it in the conversation, put it in a command argument, or print it.
Load this Skill to expose its MCP tools. Inspect the discovered input schema and configuration only. This Skill has no free model-list tool; do not generate an image as an installation test.

## Generation and retrieval

1. Confirm the user wants this image operation and accepts its [current pricing](https://platform.acedata.cloud/models?utm_source=amp&utm_medium=integration&utm_campaign=evergreen&utm_content=nano-banana_amp_pricing), parameters and output count. Choose a currently supported model and parameters with the user; do not silently substitute models, providers, prices, or resolution tiers.
2. Call `nanobanana_generate_image` exactly once for that requested operation. Use an edit tool only when the user provides authorized reference media and asks to edit it.
3. Save the returned task ID. Call `nanobanana_get_task(task_id="<original task ID>")` to retrieve the same task after pending results, disconnects or timeouts. Never submit generation again merely to poll.
4. Require an explicit terminal success (`state=complete` with success, or the returned finished timestamp and successful response). Failure is terminal too. A pending task or an early media URL is not completion. Do not invent IDs, output links, media availability, completion or billing. Report the final status and returned media links; preserve upstream errors (including rate limit and moderation meaning).
5. On an uncertain submission, inspect its original task/request before any new paid request. A failed result is not permission to retry, change the model, or use a fallback.

Amp reasoning can have its own usage charge. Installation/tool discovery and API metadata are distinct from inference, generation, terminal media, and the account's usage record.
