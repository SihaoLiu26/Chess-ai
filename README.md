# Chess AI Assistant

A single-file, browser-based tool for learning chess. It combines a structured
tutorial, adaptive practice against a local engine, and a conversational AI coach
that answers questions and explains your games.

## Features

- **Tutorial** — 13 short lessons from the rules to basic tactics and endgames,
  each with an interactive board and a final quiz.
- **Practice** — four opponent levels (beginner / junior / advanced / master)
  powered by a local minimax engine with alpha–beta pruning.
- **AI Assistant** — chat about rules, openings, tactics and endgames. Paste a PGN
  or send your current game; a local engine evaluates every move first, and the
  language model explains the result based on that evaluation.

## Technical notes

- One self-contained `index.html` (inline CSS/JS, no build step).
- Rules: [chess.js](https://github.com/jhlywa/chess.js) 0.10.3 via CDN.
- Practice/review engine: plain JavaScript, runs entirely on the client.
- Language model: Doubao-Seed-2.1-lite via Volcengine Ark (OpenAI-compatible API).

## Deploy on GitHub Pages

1. Create a new repository and upload the contents of this folder
   (`index.html`, `.nojekyll`, `README.md`).
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*,
   choose the `main` branch and the `/ (root)` folder, then save.
4. After a minute, the site is live at
   `https://<your-username>.github.io/<repo-name>/`.

Because GitHub Pages serves the page over HTTPS, the API's CORS policy passes
and the assistant works on any device, including phones.

## Security note

The API key is embedded in `index.html` so visitors can use the assistant without
any setup. **Anyone who opens the page can extract and reuse this key, and all
usage is billed to the key owner.** Before sharing publicly, set a usage cap in
the Volcengine Ark console, and consider moving the key behind a small backend
proxy for production use. To replace the key, edit the `EMBEDDED_ARK_KEY` line in
`index.html`.