# Developer Context: kenneth.computer

## What This Is

A personal blog migrated from a custom Python static site generator to Quartz. The goal was faster builds while preserving the original aesthetic.

## Architecture

### Repositories
- **k3nnethfrancis/kenneth-dot-computer** - Content and project files
- **k3nnethfrancis/quartz** - Forked Quartz with custom theme (submodule)

The quartz fork doesn't share git history with upstream (`jackyzha0/quartz:v4`). Upgrading to future Quartz versions requires manually re-applying customizations.

### Key Customizations in Quartz Fork

**`quartz.config.ts`**:
- Colors: Solarized-inspired palette
  - Light: cream `#f5e6c8` bg, dark teal `#002b36` text
  - Dark: deep blue `#1a1a2e` bg, light gray `#e0e0e0` text
- Typography: IBM Plex Mono throughout
- Site: `kenneth.computer`, Plausible analytics

**`quartz/styles/custom.scss`**:
- Terminal-inspired theme (sharp corners, uppercase headers)
- Profile section layout (`.profile-section`, `.social-links`)
- Link hover effects (inverted colors)

## Content Structure

```
garden/
├── index.md        ← Home page with inline HTML/CSS for profile section
├── blog/
│   ├── index.md    ← Blog listing
│   └── *.md        ← Individual posts
├── artifacts/
│   ├── index.md    ← Projects listing  
│   └── *.md        ← Project pages (agency42, talentdao, noometic)
└── images/
    ├── pfp/        ← Profile pictures
    ├── posts/      ← Blog post images
    └── quests/     ← Project images
```

## Original Blog Reference

The original Python blog is in `shoshin-dot-blog/` (gitignored, local reference only).

Original features that were preserved:
- YAML frontmatter (date, image, readTime, tags)
- Footnotes
- KaTeX math rendering
- Custom home page layout
- Archive/listing pages

## Pending Work

### Face Looker Feature
Interactive profile picture that follows cursor. Not yet implemented.

Components in `face_looker/` (gitignored):
- Python script generates 121 gaze images via Replicate API
- React hook + component for mouse tracking
- Needs conversion to vanilla JS for Quartz

### Implementation Plan
1. Generate gaze images from headshot
2. Create vanilla JS mouse tracker
3. Integrate into home page profile section

## Design Principles

- Minimal, terminal-inspired aesthetic
- Monospace typography
- High contrast (dark on cream / light on dark blue)
- No unnecessary UI chrome
- Content-first

## Build Commands

```bash
# Development
cd quartz && npx quartz build --serve --directory ../garden

# Production build
cd quartz && npx quartz build --directory ../garden
# Output: quartz/public/
```
