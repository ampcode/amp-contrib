---
name: gpt-image-by-acedatacloud
description: Generate or edit GPT Image pictures through Ace Data Cloud, using image-only tools and polling the original image task for its final result.
license: Apache-2.0
metadata:
  author: Ace Data Cloud
  version: "1.0.0"
  category: image
---

# GPT Image by Ace Data Cloud

Generate or edit GPT Image pictures through Ace Data Cloud, using image-only tools and polling the original image task for its final result.
This is an Ace Data Cloud integration, not an official GPT Image or Amp plugin endorsement.

## Setup and tool scope

Requires Amp native Skill MCP support, an existing Amp login, and `ACEDATACLOUD_API_TOKEN` in the environment that starts Amp.

Read [README.md](README.md) for installation, illustrated API-key setup, and troubleshooting.
The sibling `mcp.json` connects only `gpt-image-ace` at `https://openai.mcp.acedata.cloud/mcp` and limits tools to this service.
Reuse an existing matching connection; do not add a second server or alter unrelated settings.
Keep the API key in `ACEDATACLOUD_API_TOKEN`; never request it in the conversation, put it in a command argument, or print it.
Load this Skill to expose its MCP tools. Use `openai_list_image_models` once to inspect the supported choices; this is informational and does not prove API permissions or balance.

## Generation and retrieval

1. Confirm the user wants this image operation and accepts its [current pricing](https://platform.acedata.cloud/models?utm_source=amp&utm_medium=integration&utm_campaign=evergreen&utm_content=gpt-image_amp_pricing), parameters and output count. Always choose an explicit GPT Image model from `openai_list_image_models` that the user approves; never rely on the general image tool defaults or silently select DALL·E/Nano Banana.
2. Call `openai_generate_image` exactly once for that requested operation. Use an edit tool only when the user provides authorized reference media and asks to edit it.
3. Save the returned task ID. Call `openai_get_task(id="<original task ID>")` to retrieve the same task after pending results, disconnects or timeouts. Never submit generation again merely to poll.
4. Treat `finished_at` as terminal, then require `response.success=true` and inspect the image result; failure is terminal too. An empty task object is not success. Do not invent IDs, output links, media availability, completion or billing. Report the final status and returned media links; preserve upstream errors (including rate limit and moderation meaning).
5. On an uncertain submission, inspect its original task/request before any new paid request. A failed result is not permission to retry, change the model, or use a fallback.

Amp reasoning can have its own usage charge. Installation/tool discovery and API metadata are distinct from inference, generation, terminal media, and the account's usage record.
