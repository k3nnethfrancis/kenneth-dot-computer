# kenneth.computer

Personal website, blog, and research notes. Built with Quartz.

## Role

Claude serves as a research assistant integrated with this site. The workflow:
1. Kenneth and Claude discuss research topics (machine psychology, LLM psychometrics, etc.)
2. Insights get synthesized into notes in `garden/notes/`
3. The research log tracks the evolving arc of thinking
4. Polished findings eventually become blog posts

This is a hybrid human-AI research system. Notes are traces of thinking—raw notes, conversations, literature reviews, synthesis sessions. The goal is clear, well-reasoned information over polished writing.

## Current Research

### Machine Psychology
Applying I/O psychology methods to LLMs. Key questions:
- Do psychometric profiles (HEXACO) predict LLM behavior?
- How do profiles shift with conversation context?
- Can we infer profiles from conversation alone? (Sigmund)

See `garden/notes/machine-psychology/` and the [research log](/notes/research-log).

## Content Structure

```
garden/
├── index.md           ← Home page
├── blog/              ← Published posts
├── artifacts/         ← Project pages
├── notes/
│   ├── index.md       ← Notes overview
│   ├── research-log/  ← Dated entries tracking research arc
│   └── machine-psychology/
│       ├── psych.md   ← Framework design
│       └── *.md       ← Topic pages
└── images/
```

## Architecture

- **k3nnethfrancis/kenneth-dot-computer** - Content repo
- **k3nnethfrancis/quartz** - Forked Quartz with custom theme (submodule)

### Theme
- Terminal-inspired: IBM Plex Mono, sharp corners, uppercase headers
- Solarized palette: cream/dark teal (light), deep blue/light gray (dark)
- Config: `quartz/quartz.config.ts`, `quartz/quartz/styles/custom.scss`

### Deployment
GitHub Pages via Actions (`.github/workflows/deploy.yml`). Triggers on push to `main`.

## Commands

```bash
# Dev server
cd quartz && npx quartz build --serve --directory ../garden

# Production build
cd quartz && npx quartz build --directory ../garden
```

## Working with Notes

### Adding a research log entry
Create `garden/notes/research-log/YYYY-MM-DD.md`:
```yaml
---
title: YYYY-MM-DD
date: YYYY-MM-DD
tags:
  - machine-psychology
---

# YYYY-MM-DD | Title

Content...
```

Update `garden/notes/research-log/index.md` to include the new entry.

### Tags
| Tag | Description |
|-----|-------------|
| `machine-psychology` | Behavioral study of LLMs via psychological methods |
| `psychometrics` | Personality measurement, HEXACO profiling |

## Pending

### Face Looker
Interactive profile picture that follows cursor. Components in `face_looker/` (gitignored). Needs vanilla JS implementation for Quartz.
