# JoHex AI 配置指南

🌐 **语言**

[English](../../SETUP.md) | **简体中文** | [繁體中文（台灣）](SETUP.zh-TW.md) | [繁體中文（香港）](SETUP.zh-HK.md)  | [日本語](SETUP.ja.md) | [한국어](SETUP.ko.md) | [Français](SETUP.fr.md) | [Deutsch](SETUP.de.md)

---

## 概述

JoHex AI 允许运行在 JoHex 中的 Python 脚本通过 **OpenAI Compatible Chat Completions API** 与现代 AI 模型进行通信。

在使用任何 AI 功能之前，您需要先配置一个 AI 服务提供商。

JoHex AI **不提供 AI 模型或 API Key**，您可以使用任何兼容 OpenAI API 的 AI 服务。

支持（但不限于）以下 AI 服务：

- OpenAI
- Google Gemini
- NVIDIA Build
- DeepSeek
- OpenRouter
- Ollama
- LM Studio
- LocalAI
- vLLM
- 自建 OpenAI Compatible 服务

---

# AI 配置

在 JoHex 中打开：

```text
Options
    └── Preferences
            └── AIConfig
```

然后依次配置以下选项。

---

## Endpoint URL（接口地址）

填写 AI 服务提供商提供的 **Chat Completions Endpoint**。

例如：

```text
https://api.openai.com/v1/chat/completions
```

```text
https://integrate.api.nvidia.com/v1/chat/completions
```

```text
http://localhost:11434/v1/chat/completions
```

该接口必须支持 **Streaming（流式输出）**。

---

## API Key

输入 AI 服务提供商提供的 API Key。

例如：

```text
sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

或者

```text
nvapi-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

API Key 将仅保存在本地计算机中，仅在向您配置的 AI 服务发送请求时使用。

---

## Model（模型名称）

填写需要调用的模型名称。

例如：

```text
gpt-4.1
```

```text
meta/llama-3.3-70b-instruct
```

```text
gemini-2.5-pro
```

```text
deepseek-chat
```

```text
qwen3-235b
```

不同 AI 服务支持的模型名称可能不同，请参考对应平台提供的模型列表。

---

## Maximum Response Tokens（最大回复 Token 数）

用于限制 AI 单次生成内容的最大 Token 数。

推荐设置：

| 使用场景 | 推荐值 |
|----------|-------:|
| 快速解释 | 512 |
| 文件结构分析 | 1024 |
| 逆向分析 | 2048 |
| 详细分析报告 | 4096 |

较大的 Token 数可能增加响应时间及 API 使用成本。

---

## Maximum Upload Size（最大上传文本）

指定 JoHex 从当前文件中提取并发送给 AI 的最大文本或十六进制数据长度。

推荐值：

| 文件大小 | 推荐上传大小 |
|----------|------------:|
| 小文件 | 4096 字符 |
| 中等文件 | 8192 字符 |
| 大文件 | 16384 字符 |

上传更多内容可以为 AI 提供更多上下文，但也会增加 Token 消耗。

---

## Temperature（温度）

控制 AI 回复的随机程度。

推荐值：

```text
0.1
```

较低的 Temperature 更适合：

- 文件格式分析
- 二进制分析
- 恶意软件分析
- 逆向工程

---

## Request Timeout（请求超时）

等待 AI 返回结果的最长时间。

推荐值：

```text
60 秒
```

---

## Streaming Response（流式输出）

建议启用。

```text
启用（Enabled）
```

开启后，JoHex 将实时显示 AI 正在生成的内容，而无需等待全部完成。

---

# 配置示例

| 配置项 | 示例 |
|--------|------|
| Endpoint URL | https://integrate.api.nvidia.com/v1/chat/completions |
| API Key | nvapi-******************************** |
| Model | meta/llama-3.3-70b-instruct |
| Maximum Response Tokens | 2048 |
| Maximum Upload Size | 8192 |
| Temperature | 0.1 |
| Request Timeout | 60 秒 |
| Streaming Response | Enabled |

---

# 免费申请 API Key

JoHex AI 不提供 API Key。

您可以从任意支持 OpenAI Compatible API 的 AI 服务商申请 API Key。

如果您希望免费体验，推荐使用 **NVIDIA Build**。

下面的视频详细介绍了：

- 注册 NVIDIA 账号
- 免费申请 API Key
- 配置 Endpoint URL
- 选择模型
- 在 JoHex 中完成 AI 配置

YouTube：

https://www.youtube.com/watch?v=C59iQ9fIYyw

---

# 安全说明

您的 API Key 仅保存在本地计算机。

JoHex 仅会向您配置的 AI 服务发送请求。

除非您主动执行 AI 功能，否则不会上传任何文件内容或十六进制数据。

---

# 常见问题

## AI Connection Error（AI 连接失败）

请检查：

- Endpoint URL 是否正确
- API Key 是否正确
- 网络连接是否正常
- 防火墙是否阻止访问
- AI 服务是否正常运行

---

## Authentication Failed（身份验证失败）

请确认：

- API Key 正确
- API Key 未过期
- 当前账号拥有访问所选模型的权限

---

## Model Not Found（模型不存在）

请确认填写的模型名称与 AI 服务提供商提供的模型名称完全一致。

---

## Request Timeout（请求超时）

可能原因：

- 网络较慢
- 上传内容过大
- AI 服务繁忙

建议适当降低 **Maximum Upload Size**。

---

# 说明

JoHex AI 与具体 AI 服务提供商无关。

任何支持 **OpenAI Chat Completions API** 且支持 **Streaming** 的 AI 服务，都可以直接接入 JoHex，而无需修改 JoHex 本身。