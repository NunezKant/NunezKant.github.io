# Miguel A. Núñez Ochoa — Personal Portfolio Site
## Project brain for Claude Code

---

## What this project is

A personal portfolio / recruiter-facing website for **Miguel A. Núñez Ochoa**, a Computational Neuroscientist and ML Scientist at HHMI Janelia Research Campus. The site targets industry recruiters in healthcare AI, pharma, and biotech — specifically in **Montreal and Barcelona** — while also serving as a research presentation card.

The site is a **pure static site** (vanilla HTML + CSS + JS). No framework, no build step, no bundler. One `index.html` file is the source of truth. Deploy by pushing to GitHub → GitHub Pages serves it automatically.

---

## Target audience & goals

**Primary:** Industry recruiters at companies like AstraZeneca Barcelona, Sanofi Montreal, Oryzon Genomics, Perceiv AI, Aifred Health, IQVIA, Novartis, Roche, BSC-CNS, Grifols.

**Secondary:** Academic collaborators and conference contacts.

**The page's single job:** Convert a recruiter visit into a contact (email, LinkedIn, Google Scholar click). Every design and copy decision should serve this.

---

## Stack & file structure

```
miguel-portfolio/
├── index.html          ← entire site (HTML + CSS + JS in one file)
├── CLAUDE.md           ← this file
├── README.md           ← human-readable project notes
├── .gitignore
└── .claude/
    └── settings.json   ← Claude Code hooks
```

**Do not add a build system** unless Miguel explicitly asks for one. The single-file approach is intentional — it makes the site trivially deployable and editable.

---

## Design system (do not deviate without asking)

### Color tokens
| Name        | Hex       | Use                                      |
|-------------|-----------|------------------------------------------|
| `--navy`    | `#0A1628` | Primary background (dark sections)       |
| `--navy-mid`| `#0F2040` | Industry section background              |
| `--navy-soft`| `#162847`| Cards, stat panels                       |
| `--cream`   | `#F5F0E8` | Light section backgrounds                |
| `--cream-dim`| `#E8E2D5`| Research area cards                      |
| `--teal`    | `#00C4B3` | Primary accent — neural signal color     |
| `--teal-dim`| `#008F83` | Muted teal for light backgrounds         |
| `--gold`    | `#C9A84C` | Publication badges, standout nodes       |
| `--slate`   | `#8A9BB0` | Secondary text, labels                   |
| `--white`   | `#FFFFFF` | High-contrast headings on dark bg        |

### Typography
- **Display/headings:** `Playfair Display` (serif) — signals research credibility
- **Body:** `Inter` (sans-serif) — industry-legible
- **Monospace/data:** `JetBrains Mono` — technical credibility, used for numbers, labels, chips

### Key design principle
The **neural network canvas animation** in the hero is the signature element. It should always stay. Nodes pulse like electrophysiology recordings — this is the visual identity of the site.

---

## Content that must stay accurate (verify before editing)

| Field | Value |
|-------|-------|
| Institution | HHMI Janelia Research Campus (Pachitariu & Stringer Lab) |
| Role | Research Associate |
| Start date | Aug 2020 (CV) / Jul 2021 (LinkedIn) |
| Key stat | up to 50,000 neurons recorded simultaneously |
| Top publication | *Nature Communications* (2025), DOI: 10.1038/S41467-025-61171-9 |
| Google Scholar | https://scholar.google.com/citations?user=-atQBQgAAAAJ&hl=en |
| LinkedIn | https://www.linkedin.com/in/miguelno |
| GitHub | https://github.com/NunezKant |
| Email | miguel.nunez.ochoa@gmail.com |
| Phone | (+52) 331-043-1457 |
| Target cities | Montreal (Canada) + Barcelona (Spain) |

---

## Sections

| Section | Purpose | Background |
|---------|---------|------------|
| `#hero` | First impression — animated neural net, name, two CTAs, stats card | Dark navy |
| `#intro` | About + timeline of career. Sticky sidebar with tagline + skill chips | Cream |
| `#industry` | 6 expertise cards + role-fit table targeting pharma/health AI recruiter | Navy mid |
| `#research` | Full publication list + 3 research area cards + Google Scholar link | Cream |
| `#contact` | Email + LinkedIn + Scholar + GitHub links, target cities callout | Dark navy |

---

## Role fit targets (inform all copy decisions)

From the job target report (`job_targets_montreal_barcelona.md`):

| Role | Fit | Key companies |
|------|-----|---------------|
| Research Scientist / Senior Scientist | ⭐⭐⭐ | Oryzon, Esteve, Ferrer, BSC-CNS |
| ML Scientist / Senior AI Scientist | ⭐⭐⭐ | Perceiv AI, Aifred Health, Valence Discovery |
| Computational Scientist | ⭐⭐⭐ | BSC-CNS, AstraZeneca, Sanofi |
| Senior Data Scientist | ⭐⭐ | Novartis, Roche, GSK, IQVIA |
| Digital Health AI Scientist | ⭐⭐ | AstraZeneca, Sanofi Plai, Quibim |
| RWE Data Scientist | ⭐ (building) | IQVIA (Montreal + Barcelona) |

**Copy tone:** Translate academic framing to industry impact. E.g., not "we investigate neural circuits" but "analyzed 50K-neuron recordings using ML to identify computational mechanisms underlying cognition."

---

## Deployment

**Platform:** GitHub Pages (free, no build step needed)
**Repo name convention:** `NunezKant.github.io` → auto-serves at `https://nunezkant.github.io`
**Deploy:** `git push origin main` → GitHub Pages picks it up in ~30 seconds.

**Optional custom domain:** Point `miguelno.com` or similar via Cloudflare DNS:
- 4 A records → `185.199.108.153`, `.109.153`, `.110.153`, `.111.153`
- CNAME `www` → `nunezkant.github.io`
- Add `CNAME` file to repo root containing `yourdomain.com`

---

## What to work on next

- [ ] Add a proper headshot / photo (Miguel to provide)
- [ ] Optimize CV (see CV optimization task notes below)
- [ ] Add Open Graph / Twitter Card meta tags for link previews
- [ ] Consider a `/cv` page or downloadable PDF link
- [ ] Add Google Analytics or Plausible (privacy-respecting) once live

---

## CV optimization task (tracked here)

**Goal:** Reframe academic CV into an industry-facing document for pharma/health AI/biotech roles in Montreal and Barcelona.

**Key translation needed:**
- Academic: "We record from populations of up to 50,000 neurons and use machine learning to investigate activity patterns"
- Industry: "Designed and applied ML pipelines to large-scale neural datasets (up to 50K neurons) to extract population-level features predictive of cognitive state"

**Gaps to address:**
- EHR/claims experience (for RWE roles) → call out causal inference as transferable
- Drug discovery domain knowledge → call out the translation from neural modeling to molecular ML

**Format target:** ATS-compatible, 2 pages max, clear role-tagged summary at top.

---

## Working notes

_Use this section to track decisions, things tried, and context for future sessions._

- Site built: June 2026
- Design inspiration: andlukyane.com, kevinjmiller.org, neurokim.com
- Single-file architecture chosen for simplicity — revisit if site grows beyond 3 pages
