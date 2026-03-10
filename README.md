# LexTax — Indian International Tax Case Law Engine

A fully static, single-file web app for searching and analysing Indian international tax case law — powered by the Claude AI API. Runs entirely in the browser with **zero backend**.

🌐 **Live demo:** `https://<your-username>.github.io/<repo-name>/`

---

## Features

- **15 landmark cases** pre-loaded (Vodafone, Engineering Analysis, Azadi Bachao, etc.)
- **Daily auto-scan** — calls Claude with web search to find today's new ITAT / HC / SC judgments
- **Live search** — search any query across Indian legal databases via Claude
- **AI Analysis** — per-case expert analysis streamed from Claude
- **Weekly digest** — auto-generated practitioner digest
- **Full library** with filters (topic, court, treaty country, ruling)
- **Export** — Research notes, RIS, BibTeX, JSON

---

## Deploy to GitHub Pages in 5 Steps

### 1. Create a new GitHub repository

Go to [github.com/new](https://github.com/new) and create a **public** repository (e.g. `lextax`).

### 2. Upload the files

Either drag-and-drop in the GitHub UI, or via Git:

```bash
git clone https://github.com/<your-username>/lextax.git
cd lextax

# Copy in the files from this folder
cp index.html .
mkdir -p .github/workflows
cp deploy.yml .github/workflows/

git add .
git commit -m "Initial LexTax deployment"
git push origin main
```

### 3. Enable GitHub Pages

1. In your repo, go to **Settings → Pages**
2. Under **Source**, select **GitHub Actions**
3. Save

### 4. Trigger the deployment

The workflow in `.github/workflows/deploy.yml` runs automatically on every push to `main`.

Check **Actions** tab to watch it deploy. Takes ~30 seconds.

### 5. Visit your site

Your site will be live at:
```
https://<your-username>.github.io/<repo-name>/
```

---

## Using the App

When you open the app, you'll be asked for your **Anthropic API key**.

- Get one free at [console.anthropic.com](https://console.anthropic.com/)
- The key is stored in `sessionStorage` only — it never leaves your browser except to call `api.anthropic.com` directly
- You can skip the key to browse the 15 pre-loaded landmark cases without live features

---

## Security Note

This app calls the Anthropic API **directly from the browser**. This is fine for personal/internal use but means your API key is visible in the browser's network tab. Do **not** share your API key publicly.

For a production deployment with multiple users, you should add a small backend proxy to store the key server-side.

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| UI framework | React 18 (CDN) |
| JSX transpilation | Babel Standalone (in-browser) |
| AI / Search | Anthropic Claude API (`claude-sonnet-4-20250514`) with web search tool |
| Hosting | GitHub Pages (static) |
| Build step | **None** — single HTML file |

---

## Local Development

No build tools needed. Just open `index.html` in a browser:

```bash
# Option 1: Python simple server (avoids CORS issues)
python3 -m http.server 8080
# then open http://localhost:8080

# Option 2: Node.js
npx serve .
# then open http://localhost:3000
```

---

## File Structure

```
lextax/
├── index.html              # The entire app — single self-contained file
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions auto-deploy workflow
└── README.md
```
