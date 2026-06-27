# JoHex AI – Einrichtungsanleitung

🌐 **Sprachen**

[English](../../setup.md) | [简体中文](SETUP.zh-CN.md) | [繁體中文](SETUP.zh-TW.md) | [日本語](SETUP.ja.md) | [한국어](SETUP.ko.md) | [Français](SETUP.fr.md) | **Deutsch**

---

## Überblick

JoHex AI ermöglicht es Python-Skripten, die innerhalb von JoHex ausgeführt werden, über die OpenAI-kompatible Chat-Completions-API mit modernen KI-Modellen zu kommunizieren.

Bevor Sie KI-gestützte Funktionen nutzen können, müssen Sie einen KI-Anbieter konfigurieren.

JoHex AI stellt **kein** KI-Modell und keinen API-Schlüssel bereit. Sie können jeden OpenAI-kompatiblen KI-Dienst verwenden.

Zu den unterstützten Anbietern gehören (unter anderem):

- OpenAI
- Google Gemini
- NVIDIA Build
- DeepSeek
- OpenRouter
- Ollama
- LM Studio
- LocalAI
- vLLM
- Selbst gehostete OpenAI-kompatible Dienste

---

# KI-Konfiguration öffnen

Öffnen Sie das folgende Menü in JoHex:

```text
Options
    └── Preferences
            └── AIConfig
```

Konfigurieren Sie die folgenden Optionen.

---

## Endpunkt-URL

Geben Sie den Chat-Completions-Endpunkt Ihres KI-Anbieters an.

Beispiele:

```text
https://api.openai.com/v1/chat/completions
```

```text
https://integrate.api.nvidia.com/v1/chat/completions
```

```text
http://localhost:11434/v1/chat/completions
```

Der Endpunkt muss Streaming-Antworten unterstützen.

---

## API-Schlüssel

Geben Sie den von Ihrem KI-Dienst bereitgestellten API-Schlüssel ein.

Beispiele:

```text
sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

oder

```text
nvapi-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Der API-Schlüssel wird lokal gespeichert und nur zur Kommunikation mit dem konfigurierten KI-Anbieter verwendet.

---

## Modell

Geben Sie den Modellnamen an.

Beispiele:

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

Die verfügbaren Modellnamen hängen vom ausgewählten KI-Anbieter ab.

---

## Maximale Antwort-Token

Gibt die maximale Anzahl an Token an, die das KI-Modell erzeugt.

Empfohlene Werte:

| Szenario | Empfohlen |
|----------|------------:|
| Kurze Erklärung | 512 |
| Binäranalyse | 1024 |
| Reverse Engineering | 2048 |
| Detaillierter Bericht | 4096 |

Höhere Werte können die Antwortzeit und die API-Nutzung erhöhen.

---

## Maximale Upload-Größe

Gibt die maximale Menge an extrahiertem Text oder Hexadezimaldaten an, die an das KI-Modell gesendet wird.

Empfohlene Werte:

| Dateigröße | Upload-Größe |
|-----------|------------:|
| Klein | 4096 Zeichen |
| Mittel | 8192 Zeichen |
| Groß | 16384 Zeichen |

Größere Uploads liefern mehr Kontext, verbrauchen aber mehr Token.

---

## Temperatur

Steuert die Zufälligkeit der Antworten.

Empfohlener Wert:

```text
0.1
```

Niedrigere Werte erzeugen eine deterministischere technische Analyse.

---

## Anfrage-Zeitlimit

Maximale Wartezeit auf KI-Antworten.

Empfohlener Wert:

```text
60 Sekunden
```

---

## Streaming-Antwort

Aktiviert den Streaming-Modus.

Empfohlen:

```text
Aktiviert
```

Streaming ermöglicht es JoHex, KI-Antworten in Echtzeit anzuzeigen, während sie generiert werden.

---

# Beispielkonfiguration

| Einstellung | Beispiel |
|----------|---------|
| Endpunkt-URL | https://integrate.api.nvidia.com/v1/chat/completions |
| API-Schlüssel | nvapi-******************************** |
| Modell | meta/llama-3.3-70b-instruct |
| Maximale Antwort-Token | 2048 |
| Maximale Upload-Größe | 8192 |
| Temperatur | 0.1 |
| Anfrage-Zeitlimit | 60 Sekunden |
| Streaming-Antwort | Aktiviert |

---

# Kostenlosen API-Schlüssel erhalten

JoHex AI enthält keinen API-Schlüssel.

Sie können einen API-Schlüssel von jedem unterstützten KI-Anbieter beziehen.

Für Benutzer, die schnell loslegen möchten, bietet NVIDIA Build derzeit kostenlosen API-Zugriff für viele unterstützte Modelle.

Das folgende Video zeigt:

- Erstellen eines NVIDIA-Kontos
- Beantragen eines kostenlosen API-Schlüssels
- Konfigurieren der Endpunkt-URL
- Auswählen eines Modells
- Testen der KI-Konnektivität in JoHex

YouTube-Tutorial:

https://www.youtube.com/watch?v=C59iQ9fIYyw

---

# Sicherheit

Ihr API-Schlüssel wird lokal auf Ihrem Computer gespeichert.

JoHex sendet Anfragen ausschließlich an den von Ihnen konfigurierten KI-Anbieter.

Es werden keine Binärdaten oder Dateiinhalte hochgeladen, sofern Sie nicht ausdrücklich einen KI-Befehl ausführen.

---

# Fehlerbehebung

## KI-Verbindungsfehler

Bitte überprüfen Sie:

- Endpunkt-URL
- API-Schlüssel
- Internetverbindung
- Firewall-Einstellungen
- Verfügbarkeit des KI-Anbieters

---

## Authentifizierung fehlgeschlagen

Bitte überprüfen Sie:

- Ob Ihr API-Schlüssel gültig ist.
- Ob Ihr API-Schlüssel nicht abgelaufen ist.
- Ob Ihr Konto die Berechtigung hat, auf das ausgewählte Modell zuzugreifen.

---

## Modell nicht gefunden

Bitte überprüfen Sie, ob der konfigurierte Modellname exakt mit einem der von Ihrem KI-Dienst bereitgestellten Namen übereinstimmt.

---

## Zeitüberschreitung der Anfrage

Mögliche Ursachen:

- Langsame Netzwerkverbindung
- Große Upload-Größe
- Überlastung des KI-Anbieters

Eine Verringerung der maximalen Upload-Größe kann die Antwortgeschwindigkeit verbessern.

---

# Hinweise

JoHex AI ist anbieterunabhängig.

Jeder KI-Dienst, der die OpenAI-Chat-Completions-API mit Streaming-Unterstützung implementiert, kann integriert werden, ohne JoHex selbst zu verändern.
