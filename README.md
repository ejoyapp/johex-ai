# JoHex AI

Official AI extension for JoHex Hex Editor.

JoHex AI enables Python scripts running inside JoHex to communicate with modern AI models and agent services through a unified streaming interface.

This repository serves as the official distribution channel for the JoHex AI extension. It is used by JoHex Script Center to check for updates, download runtime packages, and manage AI extension versions automatically.

> This repository does not contain the AI runtime source code. The runtime is distributed as a versioned binary package.

---

## Features

* Streaming AI responses
* OpenAI-compatible API support
* Automatic updates through Script Center
* Manifest-based version management
* Binary runtime distribution
* AI-assisted binary analysis
* Reverse engineering assistance
* File format exploration
* Malware investigation workflows
* Digital forensics support

---

## Supported Providers

JoHex AI can connect to any OpenAI-compatible endpoint, including:

* OpenAI
* Google Gemini
* Anthropic Claude
* DeepSeek
* OpenRouter
* Ollama
* Local AI services
* Custom AI gateways
* Self-hosted agent platforms

---

## Architecture

```text
JoHex
   │
   ├── Script Center
   │
   └── JoHex AI
         │
         ├── version.json
         ├── johex_ai_core.dat
         │
         ▼
    AI Runtime
         │
         ▼
    AI Providers
         │
         ▼
 OpenAI / Gemini / Claude / DeepSeek / Ollama
```

---

## Repository Structure

```text
johex-ai/
│
├── version.json
├── README.md
└── johex_ai_core.dat
```

### version.json

Contains version information and update metadata used by JoHex Script Center.

Example:

```json
{
    "id": "johex-ai",
    "version": "1.0.0",
    "release_date": "2026-06-15",
    "min_johex": "2.0.0",
    "package": "johex_ai_core.dat",
    "sha256": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "size": 1048576
}
```

### johex_ai_core.dat

Binary runtime package used by JoHex AI.

This package contains:

* AI runtime components
* Provider adapters
* Prompt resources
* Internal metadata
* Runtime configuration

The package is intended to be downloaded and managed automatically by JoHex.

Manual modification is not recommended.

### README.md

Repository documentation and release information.

---

## Update Workflow

When JoHex starts:

```text
JoHex
   │
   ▼
Download version.json
   │
   ▼
Compare local version
   │
   ▼
Update available?
   │
   ├── No → Continue
   │
   └── Yes
          │
          ▼
Download johex_ai_core.dat
          │
          ▼
Verify SHA256
          │
          ▼
Install Runtime
          │
          ▼
Ready
```

---

## Typical Use Cases

### Binary Analysis

Analyze unknown binary structures using AI assistance.

### Reverse Engineering

Generate explanations for binary layouts, file structures, and low-level data.

### Malware Research

Inspect suspicious files and obtain contextual AI analysis.

### File Format Exploration

Understand proprietary or undocumented file formats.

### Digital Forensics

Assist investigators with binary artifact interpretation and reporting.

---

## Versioning

JoHex AI follows Semantic Versioning.

```text
MAJOR.MINOR.PATCH
```

Examples:

```text
1.0.0
1.1.0
1.1.1
2.0.0
```

### Version Rules

| Type  | Description      |
| ----- | ---------------- |
| MAJOR | Breaking changes |
| MINOR | New features     |
| PATCH | Bug fixes        |

---

## Requirements

* JoHex 2.0 or later
* Script Center enabled
* Internet access for updates
* Access to an AI provider or agent service

---

## Security

JoHex verifies downloaded packages before installation.

Supported validation mechanisms may include:

* SHA256 verification
* Package integrity checks
* Version compatibility validation

Packages that fail verification will not be installed.

---

## Release Notes

Release information is published through:

* GitHub Releases
* version.json
* Script Center update notifications

---

## License

Copyright © EJoyApp.

All rights reserved.

JoHex and JoHex AI are part of the JoHex ecosystem.

---

## About JoHex

JoHex is a professional hex editor and binary analysis platform designed for developers, reverse engineers, digital forensics investigators, and security researchers.

JoHex AI extends these capabilities with modern AI-assisted workflows, allowing users to analyze, understand, and explore binary data more efficiently.

```
```
