# 🇫🇷 French Study Buddy

[![GitHub Pages](https://img.shields.io/badge/demo-GitHub%20Pages-2ea44f?logo=github)](https://YOUR-USERNAME.github.io/french-study-buddy/)
[![No build step](https://img.shields.io/badge/build-none%20needed-blue)](#)
[![License: MIT](https://img.shields.io/badge/license-MIT-lightgrey)](LICENSE)

A single-file, no-build web app for **TCF/TEF exam prep** — chat with an
open-source LLM (Groq or local Ollama) in French, get dual-language replies
with corrections, practice pronunciation with roleplay characters, and drill
TCF-aligned grammar, listening, reading, and speaking modules.

Everything lives in `index.html`. No npm, no backend, no build step —
open it locally or deploy straight to GitHub Pages.

**➡️ [Live demo](https://YOUR-USERNAME.github.io/french-study-buddy/)** *(update this link once Pages is enabled)*

---

## Features

- **💬 Conversation coach** — chats in French, replies with a French
  response, an English translation, and a corrections breakdown of any
  grammar/vocab mistakes you made.
- **🎭 Character roleplay** — Le Médecin, Le Boulanger, L'Agent de Voyage,
  Le Serveur, L'Agent Immobilier, Le Recruteur — each starts a themed
  roleplay conversation matching real TCF/TEF interaction topics.
- **🔊 Pronunciation coach** — pick a target phrase, listen to it
  (`speechSynthesis`, `fr-FR`), record your attempt
  (`SpeechRecognition`), and get an AI evaluation: syllable breakdown,
  the relevant phonetic rule, a comparison of what you likely said vs.
  the target, and a concrete mouth/tongue-position tip.
- **📚 Full syllabus sidebar** — Compréhension orale & écrite, Structures
  de la langue (8 grammar points), Expression écrite & orale (TCF task
  types), Thèmes de société, and Phonétique — click any topic to start a
  targeted practice conversation.
- **Bring your own model** — works with [Groq](https://console.groq.com)
  (cloud, free tier) or a local [Ollama](https://ollama.com) instance.
  Your API key is saved only in your browser's `localStorage` and is
  never committed to this repo.

## Quick start

1. Open `index.html` directly, or serve it locally:
   ```bash
   python3 -m http.server 8000
   ```
2. Click **⚙️ Paramètres**, choose the Groq or Ollama preset, add your key
   (Groq only), and save.
3. Start chatting, or pick a character / sidebar topic to begin a themed
   practice session.

Full setup details (Groq key setup, the Ollama `OLLAMA_ORIGINS` CORS
requirement, deployment) are in [`SETUP.md`](SETUP.md).

## Deploying to GitHub Pages

Settings → Pages → Source: **Deploy from a branch** → Branch: `main`,
folder: `/ (root)` → Save. Live in about a minute at
`https://<your-username>.github.io/<repo-name>/`.

## Privacy note

If you deploy this publicly, each visitor must enter **their own** API
key — it's stored only in their browser. Never commit a real API key into
`index.html` or any file in this repo.

## License

MIT — do whatever you'd like with it.
