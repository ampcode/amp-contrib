# Amp 的 HappyHorse by Ace Data Cloud

独立安装的 **HappyHorse** 品牌 Skill，工具由 Ace Data Cloud 提供；不冒充服务方官方插件，也不新增 Amp 默认模型服务商。[English](README.md) · [当前价格](https://platform.acedata.cloud/models?utm_source=amp&utm_medium=integration&utm_campaign=evergreen&utm_content=happyhorse_amp_pricing)

## 1. 只安装本服务

按 [Amp 官方指南](https://ampcode.com/docs/cli) 安装并用既有账号执行 `amp login`；Ace Key 不能代替 Amp 登录。

```bash
amp skill add AceDataCloud/Skills/platforms/amp/skills/happyhorse-by-acedatacloud
```

该源码命令已随 [Ace Skills main](https://github.com/AceDataCloud/Skills/commit/6169154675fd6523ad4230c257c7f70227a7c41b) 于2026-10-19发布；登录Amp后的实际安装仍待验证。[官方 amp-contrib](https://github.com/ampcode/amp-contrib) 投稿仍待审，不能称已收录。获接纳后独立安装命令为 `amp skill add ampcode/amp-contrib/happyhorse-by-acedatacloud`；不要两份同时安装。审查本地checkout可用 `amp skill add ./platforms/amp/skills/happyhorse-by-acedatacloud --target /绝对路径/项目/.agents/skills`，当前安装器也要求 Amp 登录。

## 2. 获取专用 API Token

1. [注册或登录 Ace → Applications](https://platform.acedata.cloud/console/applications?utm_source=amp&utm_medium=integration&utm_campaign=evergreen&utm_content=happyhorse_amp_api_key)，打开 **General application**；没有时先 **Initialize General Application**。
2. 核对 HappyHorse 权限、余额与[当前价格](https://platform.acedata.cloud/models?utm_source=amp&utm_medium=integration&utm_campaign=evergreen&utm_content=happyhorse_amp_pricing)，复制 API Key，或 **Manage Keys → Create** 创建 `Amp HappyHorse` 专用 Key。
3. 按需设到期、用量和 Allowed APIs；限制时放行所需生成/编辑和查询：`/happyhorse/videos, /happyhorse/tasks`。是否有试用额度以账户显示为准。
4. 仅复制 Key 本体，不带引号、空格或 `Bearer `；`platform-...` 管理 Token 不可替代。

![真实脱敏控制台：复制Key或管理Key](https://raw.githubusercontent.com/AceDataCloud/SunoDify/8d3d03570e73324220f111f7fe343da0792a8071/_assets/tutorial/get-api-key-en.png)

![真实脱敏控制台：创建专用Key](https://raw.githubusercontent.com/AceDataCloud/SunoDify/8d3d03570e73324220f111f7fe343da0792a8071/_assets/tutorial/create-api-key-en.png)

以上复用 Dify 教程的 Ace 控制台真图（源修订 `8d3d035`，2026-10-18 核）；图中示例名称并非 Amp 配置项。

## 3. 在启动 Amp 的环境设置 Key

macOS/Linux：`export ACEDATACLOUD_API_TOKEN='YOUR_API_TOKEN'`；PowerShell：`$env:ACEDATACLOUD_API_TOKEN = 'YOUR_API_TOKEN'`。只在自己的终端替换占位符并启动 `amp`，真实 Key 不进提示词、仓库、截图或日志。`mcp.json` 仅保存环境变量引用。托管账户/团队 Skill 要在实际执行环境配置密钥，不能假定读取本机变量。

## 4. 搜索、加载并检查

执行 `amp skill list --json`，或 **Ctrl+O → skills: list**，查找 `happyhorse-by-acedatacloud`，让 Amp 加载该 Skill 后才暴露工具。`amp mcp doctor happyhorse-ace` 检查连接，`amp tools list --json` 检查当前工具。只有项目直接配置出现审批提示、确认配置后才执行 approve；不要为了测试重复创建连接。

![Amp 官方原始命令面板参考，非Ace实测](https://static.ampcode.com/docs/cli-command-palette.png)

来源 [Amp 官方快捷键文档](https://ampcode.com/docs/cli/keybindings)，2026-10-18 下载；原图拍摄日期/版本未注明，不是本服务真实使用图。`page logs` 只是日志，不能当工具入口。真实安装/加载/结果图待既有 Amp 会话验收。

首次仅检查工具，**不生成内容**。可仅查询 happyhorse_list_models 的信息；静态信息成功不证明 Key 权限或余额。 Amp 对话推理也可能收费，预算/订阅覆盖确认前只做配置和发现。

## 5. 请求一次生成，查询同一任务

由你明确选择模型/参数、接受当前价格后才调用 `happyhorse_generate_video` 一次，保存返回的 task ID。用 `happyhorse_get_task(task_id="原ID")` 继续查同一任务；pending、超时或提前出现媒体链接都不等于完成，不能重提生成来查询进度。GPT Image 应显式选用户同意的 GPT Image 型号，不能依赖通用工具默认或切去其他系列。只有明确成功终态和真实媒体链接才报告完成；失败保留原错误并确认后续动作。核对同次请求的账单，Credits 不等于美元，不保证来源转化或仅凭安装称有收入。

## 常见问题

- 看不到 Skill/工具：查安装路径、同名遮蔽、重新加载与本 Skill 是否已加载。
- 先要求登录：这是 Amp 登录，不是 Ace Key 错误。
- 401/403：查完整服务 Key、权限、有效期、限制和余额，不发出 Key。
- 429：等待并降低并发；不自动重试收费生成。
- pending：只查原 task ID；400/审核/失败：保留错误，不自动换模型/价格或fallback。

[工具源码](https://github.com/AceDataCloud/HappyHorseMCP) · [问题反馈](https://github.com/AceDataCloud/Skills/issues)。请求内容及密钥交给 Ace 服务，生成按当前价从你的 Ace 账户计费。
