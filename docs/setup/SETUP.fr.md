# Guide de configuration de JoHex AI

🌐 **Langues**

[English](../../setup.md) | [简体中文](SETUP.zh-CN.md) | [繁體中文](SETUP.zh-TW.md) | [日本語](SETUP.ja.md) | [한국어](SETUP.ko.md) | **Français** | [Deutsch](SETUP.de.md)

---

## Présentation

JoHex AI permet aux scripts Python exécutés dans JoHex de communiquer avec des modèles d'IA modernes via l'API Chat Completions compatible OpenAI.

Avant d'utiliser une quelconque fonctionnalité basée sur l'IA, vous devez configurer un fournisseur d'IA.

JoHex AI ne fournit **pas** de modèle d'IA ni de clé API. Vous pouvez utiliser n'importe quel service d'IA compatible avec OpenAI.

Les fournisseurs pris en charge comprennent (sans s'y limiter) :

- OpenAI
- Google Gemini
- NVIDIA Build
- DeepSeek
- OpenRouter
- Ollama
- LM Studio
- LocalAI
- vLLM
- Services auto-hébergés compatibles OpenAI

---

# Ouvrir la configuration de l'IA

Ouvrez le menu suivant dans JoHex :

```text
Options
    └── Preferences
            └── AIConfig
```

Configurez les options suivantes.

---

## URL du point de terminaison

Indiquez le point de terminaison Chat Completions de votre fournisseur d'IA.

Exemples :

```text
https://api.openai.com/v1/chat/completions
```

```text
https://integrate.api.nvidia.com/v1/chat/completions
```

```text
http://localhost:11434/v1/chat/completions
```

Le point de terminaison doit prendre en charge les réponses en streaming.

---

## Clé API

Saisissez la clé API fournie par votre service d'IA.

Exemples :

```text
sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

ou

```text
nvapi-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

La clé API est stockée localement et n'est utilisée que pour communiquer avec le fournisseur d'IA configuré.

---

## Modèle

Indiquez le nom du modèle.

Exemples :

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

Les noms de modèles disponibles dépendent du fournisseur d'IA sélectionné.

---

## Nombre maximal de jetons de réponse

Spécifie le nombre maximal de jetons générés par le modèle d'IA.

Valeurs recommandées :

| Scénario | Recommandé |
|----------|------------:|
| Explication rapide | 512 |
| Analyse de binaires | 1024 |
| Rétro-ingénierie | 2048 |
| Rapport détaillé | 4096 |

Des valeurs plus élevées peuvent augmenter le temps de réponse et l'utilisation de l'API.

---

## Taille maximale d'envoi

Spécifie la quantité maximale de texte extrait ou de données hexadécimales envoyées au modèle d'IA.

Valeurs recommandées :

| Taille du fichier | Taille d'envoi |
|-----------|------------:|
| Petit | 4096 caractères |
| Moyen | 8192 caractères |
| Grand | 16384 caractères |

Des envois plus volumineux fournissent davantage de contexte mais consomment plus de jetons.

---

## Température

Contrôle le caractère aléatoire des réponses.

Valeur recommandée :

```text
0.1
```

Des valeurs plus basses produisent une analyse technique plus déterministe.

---

## Délai d'expiration des requêtes

Temps d'attente maximal pour les réponses de l'IA.

Valeur recommandée :

```text
60 secondes
```

---

## Réponse en streaming

Active le mode streaming.

Recommandé :

```text
Activé
```

Le streaming permet à JoHex d'afficher les réponses de l'IA en temps réel, au fur et à mesure de leur génération.

---

# Exemple de configuration

| Paramètre | Exemple |
|----------|---------|
| URL du point de terminaison | https://integrate.api.nvidia.com/v1/chat/completions |
| Clé API | nvapi-******************************** |
| Modèle | meta/llama-3.3-70b-instruct |
| Nombre maximal de jetons de réponse | 2048 |
| Taille maximale d'envoi | 8192 |
| Température | 0.1 |
| Délai d'expiration des requêtes | 60 secondes |
| Réponse en streaming | Activé |

---

# Obtenir une clé API gratuite

JoHex AI n'inclut aucune clé API.

Vous pouvez obtenir une clé API auprès de n'importe quel fournisseur d'IA pris en charge.

Pour les utilisateurs qui souhaitent démarrer rapidement, NVIDIA Build propose actuellement un accès API gratuit pour de nombreux modèles pris en charge.

La vidéo suivante montre comment :

- Créer un compte NVIDIA
- Demander une clé API gratuite
- Configurer l'URL du point de terminaison
- Sélectionner un modèle
- Tester la connectivité de l'IA dans JoHex

Tutoriel YouTube :

https://www.youtube.com/watch?v=C59iQ9fIYyw

---

# Sécurité

Votre clé API est stockée localement sur votre ordinateur.

JoHex n'envoie de requêtes qu'au fournisseur d'IA que vous configurez.

Aucune donnée binaire ni aucun contenu de fichier n'est envoyé tant que vous n'exécutez pas explicitement une commande d'IA.

---

# Dépannage

## Erreur de connexion à l'IA

Veuillez vérifier :

- L'URL du point de terminaison
- La clé API
- La connexion Internet
- Les paramètres du pare-feu
- La disponibilité du fournisseur d'IA

---

## Échec de l'authentification

Veuillez vérifier :

- Que votre clé API est valide.
- Que votre clé API n'a pas expiré.
- Que votre compte a l'autorisation d'accéder au modèle sélectionné.

---

## Modèle introuvable

Veuillez vérifier que le nom du modèle configuré correspond exactement à l'un de ceux fournis par votre service d'IA.

---

## Délai d'expiration de la requête

Causes possibles :

- Connexion réseau lente
- Taille d'envoi importante
- Surcharge du fournisseur d'IA

Réduire la taille maximale d'envoi peut améliorer la vitesse de réponse.

---

# Remarques

JoHex AI est indépendant du fournisseur.

Tout service d'IA implémentant l'API Chat Completions d'OpenAI avec prise en charge du streaming peut être intégré sans modifier JoHex lui-même.
