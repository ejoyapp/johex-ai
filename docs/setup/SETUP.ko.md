# JoHex AI 설정 가이드

🌐 **언어**

[English](../../setup.md) | [简体中文](SETUP.zh-CN.md) | [繁體中文](SETUP.zh-TW.md) | [日本語](SETUP.ja.md) | **한국어** | [Français](SETUP.fr.md) | [Deutsch](SETUP.de.md)

---

## 개요

JoHex AI를 사용하면 JoHex 내부에서 실행되는 Python 스크립트가 OpenAI 호환 Chat Completions API를 통해 최신 AI 모델과 통신할 수 있습니다.

AI 기반 기능을 사용하기 전에 반드시 AI 제공자를 구성해야 합니다.

JoHex AI는 AI 모델이나 API 키를 제공하지 **않습니다**. OpenAI 호환 AI 서비스라면 무엇이든 사용할 수 있습니다.

지원되는 제공자에는 다음이 포함됩니다(이에 국한되지 않음):

- OpenAI
- Google Gemini
- NVIDIA Build
- DeepSeek
- OpenRouter
- Ollama
- LM Studio
- LocalAI
- vLLM
- 자체 호스팅 OpenAI 호환 서비스

---

# AI 구성 열기

JoHex 내부에서 다음 메뉴를 엽니다:

```text
Options
    └── Preferences
            └── AIConfig
```

다음 옵션을 구성하십시오.

---

## 엔드포인트 URL

AI 제공자의 Chat Completions 엔드포인트를 지정합니다.

예시:

```text
https://api.openai.com/v1/chat/completions
```

```text
https://integrate.api.nvidia.com/v1/chat/completions
```

```text
http://localhost:11434/v1/chat/completions
```

엔드포인트는 스트리밍 응답을 지원해야 합니다.

---

## API 키

AI 서비스에서 제공한 API 키를 입력합니다.

예시:

```text
sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

또는

```text
nvapi-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

API 키는 로컬에 저장되며, 구성된 AI 제공자와 통신할 때만 사용됩니다.

---

## 모델

모델 이름을 지정합니다.

예시:

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

사용 가능한 모델 이름은 선택한 AI 제공자에 따라 다릅니다.

---

## 최대 응답 토큰

AI 모델이 생성하는 최대 토큰 수를 지정합니다.

권장 값:

| 시나리오 | 권장 값 |
|----------|------------:|
| 빠른 설명 | 512 |
| 바이너리 분석 | 1024 |
| 리버스 엔지니어링 | 2048 |
| 상세 보고서 | 4096 |

값이 높을수록 응답 시간과 API 사용량이 증가할 수 있습니다.

---

## 최대 업로드 크기

AI 모델로 전송되는 추출된 텍스트 또는 16진수 데이터의 최대 양을 지정합니다.

권장 값:

| 파일 크기 | 업로드 크기 |
|-----------|------------:|
| 작음 | 4096자 |
| 중간 | 8192자 |
| 큼 | 16384자 |

업로드 크기가 클수록 더 많은 컨텍스트를 제공하지만 더 많은 토큰을 소비합니다.

---

## 온도(Temperature)

응답의 무작위성을 제어합니다.

권장 값:

```text
0.1
```

값이 낮을수록 더 결정적인(deterministic) 기술 분석 결과를 생성합니다.

---

## 요청 시간 제한

AI 응답에 대한 최대 대기 시간입니다.

권장 값:

```text
60초
```

---

## 스트리밍 응답

스트리밍 모드를 활성화합니다.

권장:

```text
활성화됨
```

스트리밍을 사용하면 JoHex가 AI 응답이 생성되는 동안 실시간으로 표시할 수 있습니다.

---

# 구성 예시

| 설정 | 예시 |
|----------|---------|
| 엔드포인트 URL | https://integrate.api.nvidia.com/v1/chat/completions |
| API 키 | nvapi-******************************** |
| 모델 | meta/llama-3.3-70b-instruct |
| 최대 응답 토큰 | 2048 |
| 최대 업로드 크기 | 8192 |
| 온도 | 0.1 |
| 요청 시간 제한 | 60초 |
| 스트리밍 응답 | 활성화됨 |

---

# 무료 API 키 받기

JoHex AI에는 API 키가 포함되어 있지 않습니다.

지원되는 AI 제공자 중 어디에서든 API 키를 발급받을 수 있습니다.

빠르게 시작하고 싶은 사용자에게는, NVIDIA Build가 현재 많은 지원 모델에 대해 무료 API 액세스를 제공하고 있습니다.

다음 영상에서 보여 주는 내용:

- NVIDIA 계정 생성
- 무료 API 키 신청
- 엔드포인트 URL 구성
- 모델 선택
- JoHex에서 AI 연결 테스트

YouTube 튜토리얼:

https://www.youtube.com/watch?v=C59iQ9fIYyw

---

# 보안

API 키는 사용자의 컴퓨터에 로컬로 저장됩니다.

JoHex는 사용자가 구성한 AI 제공자에게만 요청을 전송합니다.

사용자가 명시적으로 AI 명령을 실행하지 않는 한, 바이너리 데이터나 파일 내용은 업로드되지 않습니다.

---

# 문제 해결

## AI 연결 오류

다음을 확인하십시오:

- 엔드포인트 URL
- API 키
- 인터넷 연결
- 방화벽 설정
- AI 제공자 가용성

---

## 인증 실패

다음을 확인하십시오:

- API 키가 유효한지.
- API 키가 만료되지 않았는지.
- 계정에 선택한 모델에 대한 액세스 권한이 있는지.

---

## 모델을 찾을 수 없음

구성된 모델 이름이 AI 서비스에서 제공하는 이름과 정확히 일치하는지 확인하십시오.

---

## 요청 시간 초과

가능한 원인:

- 느린 네트워크 연결
- 큰 업로드 크기
- AI 제공자 과부하

최대 업로드 크기를 줄이면 응답 속도가 개선될 수 있습니다.

---

# 참고

JoHex AI는 제공자 독립적입니다.

스트리밍을 지원하는 OpenAI Chat Completions API를 구현한 모든 AI 서비스는 JoHex 자체를 수정하지 않고도 통합할 수 있습니다.
