# JoHex AI 設定指南

🌐 **語言**

[English](../../setup.md) | [简体中文](SETUP.zh-CN.md) | [繁體中文（台灣）](SETUP.zh-TW.md) | **繁體中文（香港）** | [日本語](SETUP.ja.md) | [한국어](SETUP.ko.md) | [Français](SETUP.fr.md) | [Deutsch](SETUP.de.md)

---

## 概覽

JoHex AI 讓執行於 JoHex 的 Python 腳本透過 **OpenAI Compatible Chat Completions API** 與現代 AI 模型進行通訊。

使用任何 AI 功能前，請先完成 AI 服務設定。

JoHex AI **不提供 AI 模型或 API Key**，您可以使用任何兼容 OpenAI API 的 AI 服務。

目前支援（包括但不限於）：

- OpenAI
- Google Gemini
- NVIDIA Build
- DeepSeek
- OpenRouter
- Ollama
- LM Studio
- LocalAI
- vLLM
- 自行部署的 OpenAI Compatible 服務

---

# AI 設定

請在 JoHex 中開啟：

```text
Options
    └── Preferences
            └── AIConfig
```

然後依次設定以下選項。

---

## Endpoint URL（API 端點）

輸入 AI 服務提供的 **Chat Completions Endpoint**。

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

輸入 AI 服務提供的 API Key。

例如：

```text
sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

或：

```text
nvapi-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

API Key 只會儲存在本機電腦，並且僅會在向您設定的 AI 服務發送請求時使用。

---

## Model（模型名稱）

輸入需要使用的模型名稱。

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

不同 AI 平台支援的模型名稱可能有所不同，請參閱相應平台的官方文件。

---

## Maximum Response Tokens（最大回覆 Token 數）

設定 AI 每次產生內容的最大 Token 數量。

建議值：

| 使用情境 | 建議值 |
|----------|-------:|
| 快速說明 | 512 |
| 檔案結構分析 | 1024 |
| 逆向工程分析 | 2048 |
| 詳細分析報告 | 4096 |

較高的 Token 值可能增加回覆時間及 API 使用成本。

---

## Maximum Upload Size（最大上傳內容）

設定 JoHex 從目前檔案擷取並傳送至 AI 的最大文字或十六進制資料長度。

建議值：

| 檔案大小 | 建議值 |
|----------|-------:|
| 小型檔案 | 4096 字元 |
| 中型檔案 | 8192 字元 |
| 大型檔案 | 16384 字元 |

提供更多內容可讓 AI 取得更完整的上下文，但亦會增加 Token 使用量。

---

## Temperature（溫度）

控制 AI 回覆內容的隨機程度。

建議值：

```text
0.1
```

較低的 Temperature 更適合：

- 檔案格式分析
- 二進制分析
- 惡意程式分析
- 逆向工程

---

## Request Timeout（請求逾時）

等待 AI 回覆的最長時間。

建議值：

```text
60 秒
```

---

## Streaming Response（串流輸出）

建議啟用。

```text
Enabled
```

啟用後，JoHex 會於 AI 產生內容時即時顯示，而無需等待整個回覆完成。

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

您可以向任何支援 OpenAI Compatible API 的 AI 平台申請 API Key。

如希望免費體驗，建議使用 **NVIDIA Build**。

以下影片詳細介紹：

- 建立 NVIDIA 帳戶
- 免費申請 API Key
- 設定 Endpoint URL
- 選擇模型
- 在 JoHex 中完成 AI 設定

YouTube：

https://www.youtube.com/watch?v=C59iQ9fIYyw

---

# 安全性

您的 API Key 僅會儲存在本機電腦。

JoHex 僅會向您設定的 AI 平台發送請求。

除非您主動執行 AI 功能，否則不會上傳任何檔案內容或十六進制資料。

---

# 疑難排解

## AI Connection Error（AI 連接失敗）

請檢查：

- Endpoint URL 是否正確
- API Key 是否正確
- 網絡連接是否正常
- 防火牆是否阻擋連接
- AI 平台是否正常運作

---

## Authentication Failed（驗證失敗）

請確認：

- API Key 有效
- API Key 未過期
- 帳戶具有存取所選模型的權限

---

## Model Not Found（找不到模型）

請確認模型名稱與 AI 平台提供的名稱完全一致。

---

## Request Timeout（請求逾時）

可能原因包括：

- 網絡速度較慢
- 上傳內容過大
- AI 平台繁忙

建議適當降低 **Maximum Upload Size**。

---

# 備註

JoHex AI 與特定 AI 平台無關。

任何支援 **OpenAI Chat Completions API** 並支援 **Streaming** 的 AI 服務，都可以直接整合至 JoHex，而無需修改 JoHex 本身。