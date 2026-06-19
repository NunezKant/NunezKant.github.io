# Hosting Guide: Miguel's Portfolio on GitHub Pages

Everything you need to go from this folder to a live website — free, with your own domain.

---

## Option A — GitHub Pages (recommended)

**Cost:** Free forever. No credit card.
**URL you get:** `https://nunezkant.github.io`
**Time to live:** ~2 minutes after first push.

### Step 1 — Create the GitHub repository

1. Go to **github.com** and sign in (or create an account — it's free).
2. Click the **+** icon → **New repository**.
3. Name it exactly: `NunezKant.github.io`
   - ⚠️ The name must match your GitHub username exactly (case-insensitive). This is the magic that makes GitHub Pages serve it at your root domain.
4. Set visibility to **Public**.
5. Do **not** check "Add a README" — your files already have one.
6. Click **Create repository**.

### Step 2 — Push the project files

Open your terminal, navigate to this folder, and run:

```bash
git init
git add .
git commit -m "Initial commit — portfolio site"
git branch -M main
git remote add origin https://github.com/NunezKant/NunezKant.github.io.git
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. In your repo on GitHub, go to **Settings → Pages**.
2. Under **Source**, select **Deploy from a branch**.
3. Choose branch: **main**, folder: **/ (root)**.
4. Click **Save**.

Your site will be live at `https://nunezkant.github.io` within about 60 seconds.

### Step 4 — Update the site later

Any time you edit `index.html` locally, just:

```bash
git add index.html
git commit -m "Update: [what you changed]"
git push
```
GitHub Pages redeploys automatically. Changes are live in ~30 seconds.

---

## Option B — Add a custom domain (e.g. miguelno.com)

**Cost:** Domain only (~$10–15/year from Namecheap or Porkbun). Hosting stays free.
**Recommended registrar:** [Porkbun](https://porkbun.com) (cheapest, clean UX)
**Recommended DNS:** [Cloudflare](https://cloudflare.com) (free, fast, adds HTTPS + protection)

### Step 1 — Buy the domain

Go to porkbun.com and search for something like:
- `miguelno.com`
- `manunezo.com`
- `nunez-ochoa.com`

### Step 2 — Add Cloudflare as DNS provider

1. Go to cloudflare.com → **Add a site** → enter your domain → choose **Free plan**.
2. Cloudflare shows you two nameserver addresses (e.g. `ada.ns.cloudflare.com`).
3. In Porkbun (or wherever you bought the domain), replace the default nameservers with Cloudflare's two nameservers.
4. Wait ~10 minutes for propagation.

### Step 3 — Add DNS records in Cloudflare

In Cloudflare DNS dashboard, add these records:

| Type  | Name | Content           | Proxy |
|-------|------|-------------------|-------|
| A     | @    | 185.199.108.153   | DNS only (grey cloud) |
| A     | @    | 185.199.109.153   | DNS only |
| A     | @    | 185.199.110.153   | DNS only |
| A     | @    | 185.199.111.153   | DNS only |
| CNAME | www  | nunezkant.github.io | DNS only |

⚠️ Keep Cloudflare proxy **disabled** (grey cloud) for GitHub Pages — GitHub needs to issue the SSL cert itself.

### Step 4 — Tell GitHub about your custom domain

1. Create a file named `CNAME` in your repo root containing just your domain:
   ```
   miguelno.com
   ```
2. In GitHub repo **Settings → Pages → Custom domain**, type `miguelno.com` and save.
3. Check **Enforce HTTPS** (GitHub issues a free certificate via Let's Encrypt).

DNS propagation can take up to 24h but is usually under 15 minutes.

---

## Using Claude Code to edit the site

### Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

### Start a session

```bash
cd miguel-portfolio
claude
```

Claude Code will read `CLAUDE.md` automatically and know exactly what the project is, the design system, target audience, and what to work on next.

### Example prompts to use with Claude Code

```
Add Open Graph meta tags so the site previews nicely when shared on LinkedIn.
```

```
Add a downloadable CV button in the contact section that links to a PDF.
```

```
The hero section feels too tall on mobile. Fix the padding so it doesn't scroll past the fold.
```

```
Update the Nature Communications publication to add a one-sentence plain-English summary below the DOI.
```

```
Add a new "Speaking" section between Research and Contact listing my FENS talk invitation and RIIAA lectures.
```

---

## Quick reference

| Thing | Where |
|-------|-------|
| Edit the site | `index.html` |
| Project context for Claude | `CLAUDE.md` |
| Deploy | `git push origin main` |
| Live URL | `https://nunezkant.github.io` |
| GitHub Pages settings | github.com → repo → Settings → Pages |
| Cloudflare DNS | dash.cloudflare.com |
