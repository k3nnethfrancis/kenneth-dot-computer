# kenneth.computer

Personal website and blog built with [Quartz](https://quartz.jzhao.xyz/).

## Setup

```bash
# Clone with submodules
git clone --recursive https://github.com/k3nnethfrancis/kenneth-dot-computer.git
cd kenneth-dot-computer

# If you forgot --recursive
git submodule update --init --recursive

# Install dependencies
cd quartz
npm install
```

## Development

```bash
cd quartz
npx quartz build --serve --directory ../garden
```

Site runs at `http://localhost:8080`

## Project Structure

```
kenneth-dot-computer/
├── garden/          ← Site content (markdown, images)
│   ├── index.md     ← Home page
│   ├── blog/        ← Blog posts
│   ├── artifacts/   ← Project pages
│   └── images/
└── quartz/          ← Quartz (git submodule)
```

## Editing Content

Edit markdown files in `garden/`, then:

```bash
git add garden/
git commit -m "Update content"
git push
```

## Editing Theme

The `quartz/` folder is a submodule pointing to [k3nnethfrancis/quartz](https://github.com/k3nnethfrancis/quartz).

```bash
cd quartz
# Make changes to styles, config, etc.
git add . && git commit -m "Update theme" && git push

# Update reference in parent repo
cd ..
git add quartz && git commit -m "Update quartz" && git push
```

Key customization files:
- `quartz/quartz.config.ts` - Site config, colors, fonts
- `quartz/quartz/styles/custom.scss` - Theme styles

## Build

```bash
cd quartz
npx quartz build --directory ../garden
# Output: quartz/public/
```

## License

Content © Kenneth Francis. Quartz is MIT licensed.

