# Project Context: kenneth.computer Blog Migration

## Overview
This project migrates the shoshin.blog (personal blog) from a custom Python static site generator to Quartz, while preserving all existing features and adding an interactive face-tracking profile picture.

## Project Structure

```
kenneth-dot-computer/
├── claude.md           ← This file
├── plan.md            ← Implementation plan
├── shoshin-dot-blog/  ← Original blog (reference only)
├── quartz/            ← Quartz installation (target platform)
└── face_looker/       ← Face tracking implementation
```

## Original Blog Tech Stack

### Build System
- **Generator**: Custom Python script (`site_generator.py`)
- **Templates**: Jinja2
- **Markdown**: Python-Markdown with extensions
- **Dev Server**: livereload (30-60 second rebuilds - main pain point)

### Content Structure
```
content/
  posts/
    *.md  ← Blog posts in markdown
```

### Markdown Features
- YAML frontmatter
- Footnotes (Python-Markdown FootnoteExtension)
- Math rendering (KaTeX via markdown_katex)
- Custom figure extension (custom_markdown_extension.py)
- Inline images
- Code blocks with syntax highlighting

### Current Properties/Metadata Format
The blog uses standard YAML frontmatter (same format as Obsidian properties):
```yaml
---
date: YYYY-MM-DD
image: /static/images/posts/[post-name].jpg
readTime: "X minutes"
tags:
  - tag1
  - tag2
---
```

**Note**: This format is natively supported by Quartz - no conversion needed. Quartz reads Obsidian-style properties directly.

## Site Features

### Home Page (`templates/index.html`)
1. **Profile Section**
   - Profile image: `/static/images/pfp/pfp.PNG`
   - Name with typing effect: "ken_"
   - Subtitle: "i/o psychologist · ai developer"
   - Social links (Blog, GitHub, X/Twitter) with SVG icons

2. **Hamburger Menu** (fixed top-right)
   - Links: blog, github, agency
   - Custom JavaScript for toggle functionality

3. **About Section**
   - Biographical paragraphs
   - Explanation of "shoshin" (beginner's mind)

4. **Featured Posts Section**
   - Curated list (defined in `site_generator.py` FEATURED_SLUGS)
   - Shows: date, short title

### Post Pages (`templates/post.html`)
1. **Header**
   - Breadcrumb nav: home / archive
   - Title with `>` prefix
   - Metadata line: date | tags | readTime

2. **Header Image**
   - From frontmatter `image` property
   - Full-width display

3. **Content**
   - Rendered markdown
   - Footnotes section (if present)
   - Image sizing: max 400px height, responsive width

4. **Footer**
   - Link back to archive

### Archive Page (`templates/archive.html`)
- Chronological list of all posts
- Shows: date, title

### Styling
- Custom CSS files:
  - `/static/css/home.css`
  - `/static/css/post.css`
- Color scheme: Minimal, monochrome
- Typography: Monospace accents, clean sans-serif
- Layout: Centered content, responsive

## Face Looker Feature

### Concept
Replace static profile picture with an interactive face that "follows" the cursor by swapping between pre-generated images of the face looking in different directions.

### Components (from face_looker repo)
1. **Image Generation**
   - Python script uses Replicate API
   - Generates 11×11 grid (121 images) of face looking in different directions
   - Input: 512×512 face image
   - Output: `gaze_px{X}_py{Y}_256.webp` files
   - Parameters: P_MIN=-15, P_MAX=15, STEP=3, SIZE=256

2. **Frontend Implementation**
   - Track mouse position relative to container
   - Calculate normalized coordinates [-1, 1]
   - Snap to grid coordinates
   - Swap image src to appropriate gaze image
   - Original: React hook (`useGazeTracking.js`) + component (`FaceTracker.jsx`)
   - **Needs conversion to**: Vanilla JS or Quartz component

## Migration Goals

### Primary Goals
1. ✅ Faster development iteration (sub-second rebuilds)
2. ✅ Maintain all existing features
3. ✅ Preserve content (markdown files)
4. ✅ Keep design aesthetic
5. ✅ Add face looker interaction

### Non-Goals
- ❌ Don't change content structure unnecessarily
- ❌ Don't add complexity for its own sake
- ❌ Don't lose any existing functionality

## Quartz Context

### What is Quartz
- Open-source static site generator (https://quartz.jzhao.xyz/)
- Built with TypeScript
- Originally designed for publishing Obsidian vaults
- Component-based architecture
- Fast builds (Vite-based)
- Supports custom components and layouts

### Key Quartz Concepts
1. **Content Collections**: Different types of content (posts, notes, etc.)
2. **Components**: Reusable UI pieces (header, footer, custom elements)
3. **Layouts**: Page templates
4. **Plugins**: Transform/process content
5. **Config**: `quartz.config.ts` for site-wide settings

## Known Constraints

### Must Preserve
1. All blog posts (9 markdown files)
2. All metadata (dates, tags, read times, images)
3. Footnotes functionality
4. Math rendering (KaTeX)
5. Image handling (header images, inline images)
6. Custom home page layout
7. Archive/listing functionality
8. Current design aesthetic

### Technical Requirements
1. Fast rebuilds (<5 seconds, ideally <1 second)
2. Support for custom JavaScript (face looker)
3. Custom component capability
4. Flexible frontmatter
5. Image optimization/handling
6. Static output (for deployment)

## Current Site Map

```
/ (index.html)
  ├─ Home page (profile, about, featured posts)

/archive.html
  ├─ All posts chronologically

/artifacts.html
  ├─ Artifacts/side projects page

/[post-slug].html (9 posts)
  ├─ bm25-is-all-you-need.html
  ├─ epochs-of-open-science.html
  ├─ extended-mind.html
  ├─ governing-the-red-planet.html
  ├─ luxury-constraints.html
  ├─ naive-ventures.html
  ├─ on-taking-gpt4-out-of-the-box.html
  ├─ truth-terminal.html
  └─ venture-into-the-noosphere.html
```

## Source Files Reference

### Original Blog
- **Site generator**: `shoshin-dot-blog/site_generator.py`
- **Templates**: `shoshin-dot-blog/templates/*.html`
- **Content**: `shoshin-dot-blog/content/posts/*.md`
- **Static assets**: `shoshin-dot-blog/static/`
- **Custom extensions**: `shoshin-dot-blog/custom_markdown_extension.py`

### Face Looker
- **Generation script**: `face_looker/main.py`
- **React hook**: `face_looker/useGazeTracking.js`
- **React component**: `face_looker/FaceTracker.jsx`
- **Styling**: `face_looker/FaceTracker.css`
- **Example**: `face_looker/examples/react-basic/`

### Quartz
- **Config**: `quartz/quartz.config.ts`
- **Components**: `quartz/quartz/components/`
- **Layouts**: `quartz/quartz/components/pages/`
- **Styles**: `quartz/quartz/styles/`
- **Plugins**: `quartz/quartz/plugins/`

## Implementation Philosophy

1. **Incremental**: Build in phases, verify each step works
2. **Content-first**: Get basic Quartz + markdown working before customization
3. **Reference, don't copy**: Look at original blog for design, rebuild in Quartz patterns
4. **Test frequently**: Use local dev server to verify changes
5. **Document**: Track what works, what doesn't, decisions made

## Success Criteria

### Phase 1: Basic Quartz
- [ ] Quartz runs locally
- [ ] Can view sample markdown files
- [ ] Build time < 5 seconds

### Phase 2: Content Migration
- [ ] All 9 blog posts imported
- [ ] Posts render with correct formatting
- [ ] Frontmatter preserved and accessible

### Phase 3: Feature Parity
- [ ] Header images display
- [ ] Metadata renders (date, tags, readTime)
- [ ] Footnotes work
- [ ] Math rendering works
- [ ] Inline images work
- [ ] Archive page lists all posts

### Phase 4: Custom Pages
- [ ] Custom home page matches original design
- [ ] Profile section (image, name, subtitle, links)
- [ ] Featured posts section
- [ ] About section
- [ ] Hamburger menu

### Phase 5: Face Looker
- [ ] Face images generated (121 images)
- [ ] Custom component created
- [ ] Mouse tracking works
- [ ] Face follows cursor smoothly
- [ ] Integrated into home page

### Final
- [ ] Design matches original aesthetic
- [ ] All features working
- [ ] Fast builds
- [ ] Ready for deployment

## Notes

- Original blog uses livereload for dev (slow rebuilds)
- Quartz uses Vite (fast hot reload)
- Face looker requires Replicate API token (~$0.01 cost)
- Original pfp is at `shoshin-dot-blog/static/images/pfp/pfp.PNG`
- Design is minimal, monochrome, typography-focused
- No framework dependencies in original (vanilla JS only)
