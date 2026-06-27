# JoHex AI セットアップガイド

🌐 **言語**

[English](../../setup.md) | [简体中文](SETUP.zh-CN.md) | [繁體中文](SETUP.zh-TW.md) | [繁體中文（香港）](SETUP.zh-HK.md) | **日本語** | [한국어](SETUP.ko.md) | [Français](SETUP.fr.md) | [Deutsch](SETUP.de.md)

---

## 概要

JoHex AI は、JoHex 上で実行される Python スクリプトから **OpenAI Compatible Chat Completions API** を利用して最新の AI モデルと通信できるようにします。

AI 機能を利用する前に、AI サービスを設定する必要があります。

JoHex AI 自体には **AI モデルや API キーは含まれていません**。OpenAI Compatible API に対応した任意の AI サービスをご利用いただけます。

対応しているサービス（例）：

- OpenAI
- Google Gemini
- NVIDIA Build
- DeepSeek
- OpenRouter
- Ollama
- LM Studio
- LocalAI
- vLLM
- OpenAI Compatible API に対応したセルフホスト環境

---

# AI の設定

JoHex の以下のメニューを開いてください。

```text
Options
    └── Preferences
            └── AIConfig
```

以下の項目を設定します。

---

## Endpoint URL（エンドポイント URL）

AI サービスが提供する **Chat Completions Endpoint** を入力します。

例：

```text
https://api.openai.com/v1/chat/completions
```

```text
https://integrate.api.nvidia.com/v1/chat/completions
```

```text
http://localhost:11434/v1/chat/completions
```

エンドポイントは **Streaming（ストリーミング応答）** に対応している必要があります。

---

## API Key

AI サービスから発行された API キーを入力します。

例：

```text
sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

または

```text
nvapi-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

API キーはローカルコンピューターに保存され、設定した AI サービスへの通信時にのみ使用されます。

---

## Model（モデル名）

使用するモデル名を入力します。

例：

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

利用可能なモデルは AI サービスによって異なります。

---

## Maximum Response Tokens（最大応答トークン数）

AI が一度に生成する最大トークン数を指定します。

推奨値：

| 用途 | 推奨値 |
|------|------:|
| 簡単な説明 | 512 |
| バイナリ解析 | 1024 |
| リバースエンジニアリング | 2048 |
| 詳細なレポート | 4096 |

大きな値を設定すると応答時間や API コストが増加する場合があります。

---

## Maximum Upload Size（最大アップロードサイズ）

AI に送信するテキストまたは 16 進データの最大サイズを指定します。

推奨値：

| ファイルサイズ | 推奨値 |
|---------------|------:|
| 小さいファイル | 4096 文字 |
| 中程度のファイル | 8192 文字 |
| 大きいファイル | 16384 文字 |

より多くのデータを送信すると AI はより多くのコンテキストを取得できますが、トークン消費量も増加します。

---

## Temperature（Temperature）

AI の応答のランダム性を制御します。

推奨値：

```text
0.1
```

低い値は以下の用途に適しています。

- ファイル形式の解析
- バイナリ解析
- マルウェア解析
- リバースエンジニアリング

---

## Request Timeout（リクエストタイムアウト）

AI の応答を待機する最大時間を指定します。

推奨値：

```text
60 秒
```

---

## Streaming Response（ストリーミング応答）

有効にすることを推奨します。

```text
Enabled
```

有効にすると、AI が生成中の内容をリアルタイムで表示できます。

---

# 設定例

| 項目 | 設定例 |
|------|--------|
| Endpoint URL | https://integrate.api.nvidia.com/v1/chat/completions |
| API Key | nvapi-******************************** |
| Model | meta/llama-3.3-70b-instruct |
| Maximum Response Tokens | 2048 |
| Maximum Upload Size | 8192 |
| Temperature | 0.1 |
| Request Timeout | 60 秒 |
| Streaming Response | Enabled |

---

# 無料で API キーを取得する方法

JoHex AI には API キーは含まれていません。

OpenAI Compatible API を提供する任意の AI サービスから API キーを取得してください。

無料で試したい場合は **NVIDIA Build** をおすすめします。

以下の動画では次の内容を紹介しています。

- NVIDIA アカウントの作成
- 無料 API キーの取得
- Endpoint URL の設定
- モデルの選択
- JoHex での AI 接続テスト

YouTube：

https://www.youtube.com/watch?v=C59iQ9fIYyw

---

# セキュリティ

API キーはローカルコンピューターに保存されます。

JoHex は設定した AI サービスに対してのみリクエストを送信します。

AI 機能を実行しない限り、ファイル内容や 16 進データが送信されることはありません。

---

# トラブルシューティング

## AI Connection Error（AI 接続エラー）

以下をご確認ください。

- Endpoint URL
- API キー
- インターネット接続
- ファイアウォール設定
- AI サービスの稼働状況

---

## Authentication Failed（認証エラー）

以下をご確認ください。

- API キーが有効であること
- API キーの有効期限が切れていないこと
- 選択したモデルを利用する権限があること

---

## Model Not Found（モデルが見つかりません）

入力したモデル名が AI サービスで提供されている名称と完全に一致していることを確認してください。

---

## Request Timeout（タイムアウト）

考えられる原因：

- ネットワークが遅い
- アップロードサイズが大きすぎる
- AI サービスが混雑している

必要に応じて **Maximum Upload Size** を小さくしてください。

---

# 備考

JoHex AI は特定の AI サービスに依存しません。

**OpenAI Chat Completions API** と **Streaming** に対応した AI サービスであれば、JoHex を変更することなく利用できます。
