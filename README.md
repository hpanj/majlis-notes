# Majlis Notes

A small note-taking app for listening to talks: type notes as you go, then synthesize
them into a short summary with related Qur'an verses and Hadith. Everything is
searchable and saved on your own device.

This is a single static `index.html` file — no build step, no server, no framework
install required.

## Run it locally

Just open `index.html` in a browser. That's it.

## Put it on GitHub

1. Create a new repository on GitHub (e.g. `majlis-notes`).
2. Add these two files (`index.html`, `README.md`) to it and push:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/majlis-notes.git
   git push -u origin main
   ```
3. Turn on GitHub Pages: repo **Settings → Pages → Source → Deploy from branch →
   main / (root)**. Save.
4. After a minute or two, your app is live at:
   `https://<your-username>.github.io/majlis-notes/`

## Using it on your iPhone

Open the GitHub Pages link in Safari, tap the Share icon, then **Add to Home
Screen**. It'll behave like a regular app icon and open full-screen.

## About the AI synthesis feature

Synthesizing notes calls Claude's API directly from your browser. You'll need
your own Anthropic API key:

1. Get one at [console.anthropic.com](https://console.anthropic.com) (API Keys →
   Create Key). This requires a billing method on the account; usage is billed
   per API call, typically fractions of a cent per synthesis.
2. In the app, tap **Set API key** and paste it in.

Your key is stored only in your browser's local storage on your own device and
is sent only to `api.anthropic.com` — never to any third party or server of
ours, because there is no server; this is a static page.

**Important:** don't publish your deployed GitHub Pages link anywhere public
with the expectation that the key stays private — anyone using your API key
input field is putting *their own* key in *their own* browser, but if you ever
hard-code a key into the file itself rather than typing it into the input,
anyone who opens the page (or views the page source) could read and use it.
Keep the file as-is (key entered at runtime, not committed to the repo) and
you're fine.

## Data & storage

Notes and summaries are saved to your browser's `localStorage`, scoped to
this page. That means:

- Your data stays on your device — nothing is uploaded anywhere.
- It's tied to that specific browser. Safari on your iPhone and Chrome on your
  laptop won't share notes with each other — each device/browser keeps its
  own copy.
- Clearing your browser's site data for this page will erase your notes, so
  it's worth occasionally backing up anything important (e.g. copy-paste into
  a note or export feature, if you add one later).

## A note on accuracy

The app deliberately paraphrases Qur'an and Hadith rather than quoting
verbatim, and is instructed not to invent specific ayah or hadith numbers it
isn't confident about. Even so, always verify any reference against a trusted
source such as [quran.com](https://quran.com) or [sunnah.com](https://sunnah.com)
before relying on or sharing it.
