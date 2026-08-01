# French Study Buddy

A single-file, no-build web app for TCF prep: chat with an open-source LLM
(Groq or local Ollama) in French, get dual-language replies with
corrections, listen to French audio, speak your answers, and drill
TCF-aligned pronunciation/grammar/dialogue modules from the sidebar.

Everything lives in `index.html` — no npm, no build step, no server code.

## 1. Run it locally

Just double-click `index.html`, or for the most reliable experience, serve
it from a tiny local server (avoids rare browser quirks with `file://`
origins):

```
python3 -m http.server 8000
```

then open `http://localhost:8000/`.

## 2. Get a model connected

Click **⚙️ Paramètres** (top right). Pick one path:

### Option A — Groq (cloud, easiest)
1. Create a free key at https://console.groq.com/keys
2. Click the **☁️ Groq (cloud)** preset button — it fills in the Base URL
   (`https://api.groq.com/openai/v1/chat/completions`) and a model name
   (`llama-3.3-70b-versatile`).
3. Paste your key into **API Key**.
4. Click **Tester la connexion**, then **Enregistrer**.

### Option B — Ollama (local, private, free, offline)
1. Install Ollama: https://ollama.com
2. Pull a model: `ollama pull llama3`
3. **Important — CORS:** Ollama blocks browser requests by default. Start
   it with your page's origin allowed:
   ```
   OLLAMA_ORIGINS="*" ollama serve
   ```
   (On macOS/Linux you can also `launchctl setenv OLLAMA_ORIGINS "*"` then
   restart Ollama; on Windows set it as a system environment variable.)
   Using `"*"` is fine for local personal use; for anything public, set it
   to your exact site origin instead.
4. Click the **💻 Ollama (local)** preset — fills in
   `http://localhost:11434/v1/chat/completions` and `llama3`, key left as
   a harmless placeholder (Ollama ignores it).
5. Click **Tester la connexion**, then **Enregistrer**.

Your key/URL/model are saved only in your browser's `localStorage` — they
are never written into the site's files or sent anywhere except the URL
you configured.

**Security note:** if you deploy this publicly, don't share a link with
your key already saved in *your* browser — that only protects you, not
someone using their own browser on the same page. Each visitor enters
their own key locally. Never commit a key into `index.html` itself.

## 3. Push to GitHub

```bash
git init
git add index.html
git commit -m "French Study Buddy"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

(If you already have a repo, just copy `index.html` in, commit, and push.)

## 4. Turn on GitHub Pages

1. On GitHub, go to your repo → **Settings** → **Pages**.
2. Under **Source**, choose **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)` → **Save**.
4. After a minute, your app is live at
   `https://<your-username>.github.io/<your-repo>/`.

Note: if you deploy to GitHub Pages and want to use it with **Ollama**,
Ollama has to be running on *your own machine* while you use the page —
the browser will call `http://localhost:11434` locally, so this only works
for you, on your own computer, not for other visitors to the page. For a
tool other people can use without running anything locally, use the Groq
option instead.

## Notes on the response format

The system prompt asks the model to reply with three labeled sections
(`FRANÇAIS:`, `ENGLISH:`, `CORRECTIONS:`), which the app parses into the
French text, English translation, and a corrections callout. Strong models
(Llama 3.3 70B, Mistral Large, etc.) follow this reliably. If you use a
small/local model that doesn't follow instructions well, the app falls back
to showing the raw reply rather than breaking — you'll see a small note
when that happens.
