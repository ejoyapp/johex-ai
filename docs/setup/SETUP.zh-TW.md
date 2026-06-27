# JoHex AI 設定指南

🌐 **語言**

[English](../../setup.md) | [简体中文](SETUP.zh-CN.md) | **繁體中文（台灣）** | [繁體中文（香港）](SETUP.zh-HK.md)  | [日本語](SETUP.ja.md) | [한국어](SETUP.ko.md) | [Français](SETUP.fr.md) | [Deutsch](SETUP.de.md)

---

## 概述

JoHex AI 可讓執行於 JoHex 中的 Python 指令碼透過 **OpenAI Compatible Chat Completions API** 與現代 AI 模型進行通訊。

在使用任何 AI 功能之前，請先設定 AI 服務提供者。

JoHex AI **不提供 AI 模型或 API Key**，您可以使用任何相容於 OpenAI API 的 AI 服務。

支援（但不限於）以下 AI 服務：

- OpenAI
- Google Gemini
- NVIDIA Build
- DeepSeek
- OpenRouter
- Ollama
- LM Studio
- LocalAI
- vLLM
- 自行架設的 OpenAI Compatible 服務

---

# AI 設定

在 JoHex 中開啟：

```text
Options
    └── Preferences
            └── AIConfig
```

接著依序設定下列選項。

---

## Endpoint URL（端點網址）

填入 AI 服務提供者所提供的 **Chat Completions Endpoint**。

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

此端點必須支援 **Streaming（串流輸出）**。

---

## API Key

輸入 AI 服務提供者提供的 API Key。

例如：

```text
sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

或

```text
nvapi-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

API Key 僅會儲存在本機電腦中，並且只會在向您設定的 AI 服務發送請求時使用。

---

## Model（模型名稱）

填入要使用的模型名稱。

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

可使用的模型名稱依您所選擇的 AI 服務而有所不同，請參考對應平台提供的模型清單。

---

## Maximum Response Tokens（最大回應 Token 數）

限制 AI 單次產生內容的最大 Token 數。

建議設定：

| 使用情境 | 建議值 |
|----------|-------:|
| 快速說明 | 512 |
| 檔案結構分析 | 1024 |
| 逆向工程分析 | 2048 |
| 詳細分析報告 | 4096 |

較大的 Token 數可能增加回應時間與 API 使用成本。

---

## Maximum Upload Size（最大上傳內容）

指定 JoHex 從目前檔案擷取並傳送至 AI 的最大文字或十六進位資料長度。

建議值：

| 檔案大小 | 建議上傳大小 |
|----------|------------:|
| 小型檔案 | 4096 字元 |
| 中型檔案 | 8192 字元 |
| 大型檔案 | 16384 字元 |

上傳更多內容可提供 AI 更完整的上下文，但也會消耗更多 Token。

---

## Temperature（溫度）

控制 AI 回覆內容的隨機程度。

建議值：

```text
0.1
```

較低的 Temperature 更適合：

- 檔案格式分析
- 二進位分析
- 惡意程式分析
- 逆向工程

---

## Request Timeout（請求逾時）

等待 AI 回應的最長時間。

建議值：

```text
60 秒
```

---

## Streaming Response（串流輸出）

建議啟用。

```text
啟用（Enabled）
```

啟用後，JoHex 將於 AI 產生內容時即時顯示，而不必等待整個回應完成。

---

# 設定範例

| 設定項目 | 範例 |
|----------|------|
| Endpoint URL | https://integrate.api.nvidia.com/v1/chat/completions |
| API Key | nvapi-******************************** |
| Model | meta/llama-3.3-70b-instruct |
| Maximum Response Tokens | 2048 |
| Maximum Upload Size | 8192 |
| Temperature | 0.1 |
| Request Timeout | 60 秒 |
| Streaming Response | Enabled |

---

# 免費申請 API Key

JoHex AI 不提供 API Key。

您可以向任何支援 OpenAI Compatible API 的 AI 服務提供者申請 API Key。

若希望免費體驗，建議使用 **NVIDIA Build**。

以下影片詳細介紹：

- 建立 NVIDIA 帳號
- 免費申請 API Key
- 設定 Endpoint URL
- 選擇模型
- 在 JoHex 中完成 AI 設定

YouTube：

https://www.youtube.com/watch?v=C59iQ9fIYyw

---

# 安全性

您的 API Key 僅儲存在本機電腦。

JoHex 僅會向您設定的 AI 服務發送請求。

除非您主動執行 AI 功能，否則不會上傳任何檔案內容或十六進位資料。

---

# 常見問題

## AI Connection Error（AI 連線失敗）

請確認：

- Endpoint URL 是否正確
- API Key 是否正確
- 網路連線是否正常
- 防火牆是否阻擋連線
- AI 服務是否正常運作

---

## Authentication Failed（驗證失敗）

請確認：

- API Key 是否有效
- API Key 是否已過期
- 您的帳號是否具有存取所選模型的權限

---

## Model Not Found（找不到模型）

請確認所填寫的模型名稱與 AI 服務提供者所提供的名稱完全一致。

---

## Request Timeout（請求逾時）

可能原因包括：

- 網路速度較慢
- 上傳內容過大
- AI 服務忙碌中

建議適當降低 **Maximum Upload Size**。

---

# 說明

JoHex AI 與特定 AI 服務提供者無關。

任何支援 **OpenAI Chat Completions API** 且支援 **Streaming** 的 AI 服務，都可以直接整合至 JoHex，而無需修改 JoHex 本身。