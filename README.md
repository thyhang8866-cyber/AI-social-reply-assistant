# 社交破冰回复助手

一个本地 Windows 社交破冰回复工具。输入对方上一句话，选择关系阶段、回复风格和回复目标后，生成 5 条自然、克制、像真人微信聊天的候选回复。

## 功能特点

- 支持关系阶段：刚认识、暧昧、恋爱中、挽回
- 支持回复风格：温柔、幽默、高情商、撩人、克制
- 支持回复目标：自动判断、继续聊天、幽默接梗、安慰对方、表达喜欢、拒绝但不伤人、降温边界
- 支持本地模板模式，无需联网也能生成
- 支持 AI 增强模式，可通过环境变量接入 SiliconFlow 或 OpenAI
- 每次生成 5 条回复，每条控制在 40 字以内
- 内置过滤规则，避免低俗、PUA、强迫、道德绑架和过度讨好表达

## 下载使用

建议在 GitHub Releases 中下载发布版：

1. 打开仓库的 `Releases`
2. 下载 `社交破冰回复助手.exe`
3. 双击运行

如果没有配置 AI Key，软件会自动使用本地模式。

## AI 模式配置

软件不会读取 `.env`，也不会保存或打印 API Key。请只通过系统环境变量配置。

SiliconFlow：

```powershell
setx SILICONFLOW_API_KEY "你的API密钥"
```

可选模型配置：

```powershell
setx SILICONFLOW_MODEL "Qwen/Qwen3-8B"
```

OpenAI 备用：

```powershell
setx OPENAI_API_KEY "你的API密钥"
```

配置后需要关闭并重新打开软件，新的环境变量才会生效。

## 本地构建

需要安装 .NET 10 SDK。

构建：

```powershell
dotnet build tools\social_reply_assistant_gui\SocialReplyAssistantGui.csproj -c Release
```

发布单文件：

```powershell
dotnet publish tools\social_reply_assistant_gui\SocialReplyAssistantGui.csproj -c Release -r win-x64 --self-contained false -p:PublishSingleFile=true -o dist\social_reply_assistant_gui_publish
```

发布后生成：

```text
dist\social_reply_assistant_gui_publish\SocialReplyAssistant.exe
```

可以将该文件重命名为：

```text
社交破冰回复助手.exe
```

并上传到 GitHub Releases。

## GitHub 上传建议

- 仓库代码区：上传源码、README、项目文件
- Releases：上传 `社交破冰回复助手.exe`
- Packages：当前项目暂时不需要使用

不要把 API Key、`.env`、Token、Cookie 上传到 GitHub。

## 项目结构

```text
tools/social_reply_assistant_gui/
  Program.cs
  SocialReplyAssistantGui.csproj

dist/
  社交破冰回复助手.exe
```

## 免责声明

本工具只生成可复制的聊天建议，不会自动发送消息。生成内容应按真实关系和具体语境自行调整。

