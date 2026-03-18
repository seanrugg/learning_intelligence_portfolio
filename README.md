# Learning Intelligence Portfolio

A public-facing AI work portfolio that surfaces applied competency evidence from real AI-assisted sessions — structured problem-solving, analytical depth, and strategic thinking demonstrated in practice.

**Live demo:** `https://yourusername.github.io/learning-intelligence-portfolio`

---

## What This Is

This is the **employer-facing portfolio version** of the Learning Intelligence Dashboard. Unlike the internal dashboard (which requires manual file loading), this version:

- Automatically loads all session JSON files listed in `sessions/manifest.json`
- Requires no login, no uploads — employers just open the URL
- Updates automatically when you push new session files
- Shows an aggregated view across all sessions plus individual session drill-downs

---

## Repository Structure

```
learning-intelligence-portfolio/
├── index.html                     ← The portfolio page (deploy this)
├── sessions/
│   ├── manifest.json              ← List of all session files to load
│   ├── session-20260223-AILEARNING-7K2X.json
│   ├── moodle_ai_agent_project.json
│   └── ... (add new sessions here)
└── README.md
```

---

## Setup: GitHub Pages (Recommended)

### Step 1 — Create the repository

1. Go to [github.com/new](https://github.com/new)
2. Name it `learning-intelligence-portfolio` (or any name you prefer)
3. Set visibility to **Public**
4. Click **Create repository**

### Step 2 — Upload files

Upload the following to your repo:
- `index.html` → repo root
- `sessions/manifest.json` → `sessions/` folder
- All your session JSON files → `sessions/` folder

Or use git:
```bash
git clone https://github.com/yourusername/learning-intelligence-portfolio
cd learning-intelligence-portfolio
# copy in your files
git add .
git commit -m "Initial portfolio deploy"
git push
```

### Step 3 — Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages**
2. Under **Source**, select **Deploy from a branch**
3. Choose **main** branch, **/ (root)** folder
4. Click **Save**
5. Wait ~60 seconds, then visit: `https://yourusername.github.io/learning-intelligence-portfolio`

### Step 4 — Personalize the portfolio

Open `index.html` and edit the `CONFIG` block near the top of the `<script>` section:

```javascript
const CONFIG = {
  baseUrl: "https://yourusername.github.io/learning-intelligence-portfolio",
  manifestPath: "sessions/manifest.json",
  identity: {
    name: "Your Full Name",
    title: "Your Professional Title / Focus Areas",
    tagline: `Your custom tagline here.`
  },
  githubUrl: "https://github.com/yourusername/learning-intelligence-portfolio",
};
```

---

## Adding New Sessions

When you complete a session and generate a JSON file:

1. Add the JSON file to the `sessions/` folder in your repo
2. Add its path to `sessions/manifest.json`:

```json
{
  "sessions": [
    "sessions/existing-session.json",
    "sessions/new-session-20260318-TOPIC-XXXX.json"
  ]
}
```

3. Commit and push — the portfolio updates automatically within ~60 seconds

---

## Sharing the Portfolio

- **Full URL:** `https://yourusername.github.io/learning-intelligence-portfolio`
- **Custom domain:** GitHub Pages supports custom domains (e.g., `portfolio.yourname.com`) — see [GitHub Pages custom domain docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- **Link in resume/LinkedIn:** Add the URL directly — employers can open it in any browser with no login required

---

## Local Development

To test locally before pushing (required because `fetch()` needs a server):

```bash
# Option 1: Node.js
npx serve .

# Option 2: Python
python -m http.server 8000

# Then open: http://localhost:8000
```

> **Note:** Opening `index.html` directly from the filesystem (file://) will not work due to browser CORS restrictions on `fetch()`. Always use a local server.

---

## Session JSON Schema

Sessions are generated using the **Learning Intelligence Session Analyzer prompt** (`session-analyzer-prompt.md`). Schema version: **1.0**.

See the full schema reference in the project documentation.

---

## License

MIT — free to use, fork, and adapt.
