# kenneth.computer

This is the self-contained website repository managed by Exograph.

- `quartz/`, `plugins/`, and `quartz.config.yaml`: Quartz 5 and the customized site design.
- `garden/`: exported publishable notes and assets. Edit the original notes in Exograph.
- `.github/workflows/exograph-publish.yml`: builds an exact reviewed publication and deploys GitHub Pages.
- `scripts/`: site-specific build compatibility and regression checks.
- `exograph-site.json`: managed-site identity; `exograph-publishing.json`: generated route definitions.

Use Exograph Settings → Publishing to customize, prepare, and publish. Changes do not deploy automatically.
The local editable checkout lives under Exograph's `published-sites/` directory.
Dependencies are pinned by `package-lock.json`; use Node 24 and `npm ci`.
See [PUBLISHING.md](PUBLISHING.md) for build and content-boundary details.

Quartz is MIT licensed; see [LICENSE.txt](LICENSE.txt).
