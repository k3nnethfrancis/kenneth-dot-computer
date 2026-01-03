# kenneth.computer

Personal website, blog, and research notes of Kenneth Cavanagh. Built with Quartz.

## Role

This Claude assists with:
1. **Website engineering** - Quartz customization, publishing workflow, site maintenance
2. **Content publishing** - Formatting, frontmatter, linking between notes
3. **Research reference** - The published research lives here; the raw exploration happens in shoshin-codex

For deep research collaboration, Kenneth works with Shoshin in `/Users/kenneth/Desktop/lab/notes/shoshin-codex/`. This vault is the published output - cleaner, more synthesized, but not the primary thinking space.

---

## Status

### Git Tracking
- **This repo** - GitHub (k3nnethfrancis/kenneth-dot-computer)
- **quartz/** - Submodule (k3nnethfrancis/quartz)

### Symlink Setup (ACTIVE)
`garden/notes/` is a symlink to `shoshin-codex/garden/notes/`. This means:
- Edit notes in shoshin-codex, they appear here automatically
- `draft: true` frontmatter prevents publishing (Quartz filters drafts)
- Other garden content (blog/, artifacts/, index.md) is native to this repo

```
garden/
├── notes/     → symlink to shoshin-codex/garden/notes/
├── blog/      → native to this repo
├── artifacts/ → native to this repo
└── index.md   → native to this repo
```

### Publishing Protocol
- **Notes**: Edit in shoshin-codex/garden/notes/, appears here via symlink
- **Blog/Artifacts**: Edit directly here
- Use `draft: true` in frontmatter to hide content from publishing

---

## Content Structure

```
garden/
├── index.md              ← Home page
├── blog/                 ← Published posts
├── artifacts/            ← Project pages (agency42, noometic, etc.)
├── notes/
│   ├── index.md          ← Notes overview
│   ├── research-log/     ← Dated entries tracking research arc
│   ├── machine-psychology/
│   │   ├── index.md      ← Topic overview
│   │   ├── psych.md      ← Psych framework design
│   │   ├── sigmund.md    ← Sigmund architecture
│   │   └── *.md          ← Topic pages
│   ├── cybernetics/      ← Systems thinking notes
│   └── agent-simulations/
└── images/
```

## Current Research (Reference)

### Machine Psychology

Applying I/O psychology methods to LLMs. Key questions:
- Do psychometric profiles (HEXACO) predict LLM behavior?
- How do profiles shift with conversation context?
- Can we infer profiles from conversation alone? (Sigmund)

Active code: `/Users/kenneth/Desktop/lab/projects/research/psych-eval/`

---

## Architecture

- **k3nnethfrancis/kenneth-dot-computer** - Content repo
- **k3nnethfrancis/quartz** - Forked Quartz with custom theme (submodule)

### Theme

Terminal-inspired: IBM Plex Mono, sharp corners, uppercase headers. Solarized palette.
- Config: `quartz/quartz.config.ts`
- Styles: `quartz/quartz/styles/custom.scss`

### Deployment

GitHub Pages via Actions (`.github/workflows/deploy.yml`). Triggers on push to `main`.

---

## Commands

```bash
# Dev server
cd quartz && npx quartz build --serve --directory ../garden

# Production build
cd quartz && npx quartz build --directory ../garden
```

---

## Content Conventions

### Research Log Entry

```markdown
---
title: YYYY-MM-DD
date: YYYY-MM-DD
tags:
  - research-log
  - [topic-tags]
---

# YYYY-MM-DD | Session Title

[Content...]
```

Update `garden/notes/research-log/index.md` to include new entries.

### Tags

| Tag | Description |
|-----|-------------|
| `machine-psychology` | Behavioral study of LLMs via psychological methods |
| `psychometrics` | Personality measurement, HEXACO profiling |
| `cybernetics` | Systems thinking, feedback loops, requisite variety |

---

## Pending

### Face Looker
Interactive profile picture that follows cursor. Components in `face_looker/` (gitignored). Needs vanilla JS implementation for Quartz.
