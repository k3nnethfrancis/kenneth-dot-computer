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

### Git Tracking (Three Repos)

| Repo | Location | Remote |
|------|----------|--------|
| kenneth-dot-computer | This repo | GitHub (k3nnethfrancis/kenneth-dot-computer) |
| quartz | Submodule at `quartz/` | GitHub (k3nnethfrancis/quartz), branch `v4` |
| shoshin-codex | `../shoshin-codex/` | GitHub (k3nnethfrancis/shoshin-codex), private |

### Local Development

`garden/research/` is a symlink to `shoshin-codex/garden/research/`. Edit research in shoshin-codex, see changes locally via symlink.

### Deployment

GitHub Actions (`.github/workflows/deploy.yml`) does a multi-repo checkout:
1. Checks out kenneth-dot-computer
2. Checks out shoshin-codex (via `SHOSHIN_CODEX_TOKEN` secret)
3. Copies `vault/garden/research/` to `garden/research/`
4. Builds with Quartz

This means the symlink works locally but deployment pulls fresh from shoshin-codex.

### Commit Workflows

**Site content/config changes** (garden/, quartz config):
```bash
# In kenneth-dot-computer
git add . && git commit -m "message" && git push
# → Auto-deploys via GitHub Actions
```

**Research content changes** (shoshin-codex/garden/research/):
```bash
# In shoshin-codex
git add . && git commit -m "message" && git push
# Then trigger deploy: push to kenneth-dot-computer OR manually run workflow
```

**Quartz customizations** (styles, components, layout):
```bash
# 1. Commit in submodule
cd quartz
git add . && git commit -m "message" && git push origin v4

# 2. Update parent's reference
cd ..
git add quartz && git commit -m "update quartz" && git push
# → Auto-deploys
```

### Publishing Protocol
- **Research**: Edit in shoshin-codex/garden/research/, push both repos
- **Blog/Homepage**: Edit directly here, push
- Use `draft: true` in frontmatter to hide content

---

## Content Structure

```
garden/
├── index.md              ← Home page
├── blog/                 ← Published posts
├── research/             ← Research notes (symlinked from shoshin-codex)
│   ├── index.md          ← Research questions overview
│   ├── logs/             ← Dated entries tracking research arc
│   ├── artifacts/        ← Things built (Miniverse, Sigmund, experiments)
│   └── notes/            ← Lit reviews, methodology, theory
└── images/
```

## Current Research (Reference)

### Research Questions

1. **RQ1**: How do humans understand and stay in control of multi-agent AI systems?
2. **RQ2**: Can models learn to reason reliably about psychological states?
3. **RQ3**: Can reasoning models learn to model psychometrics?

Active code: `/Users/kenneth/Desktop/lab/projects/research/`

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

Update `garden/research/logs/index.md` to include new entries.

### Tags

| Tag | Description |
|-----|-------------|
| `machine-psychology` | Behavioral study of LLMs via psychological methods |
| `research` | Research arc content |
| `cybernetics` | Systems thinking, feedback loops, requisite variety |

---

## Pending

### Face Looker
Interactive profile picture that follows cursor. Components in `face_looker/` (gitignored). Needs vanilla JS implementation for Quartz.
