# kenneth.computer

This repository holds the public website's sanitized Markdown and assets in
`garden/`, plus its reviewed GitHub Pages workflow and shared Quartz build runner. The source notes live in the
private shoshin-codex workspace. Quartz and the custom theme live separately in
[k3nnethfrancis/quartz](https://github.com/k3nnethfrancis/quartz).

Exo prepares a sanitized snapshot from the selected publication folder. An
explicit Publish action advances the `publication` branch with a normal commit,
then dispatches `.github/workflows/exograph-publish.yml` on `main` with the exact
content and engine commit IDs. Publishing does not create a branch for every
update, import private note history, or deploy automatically on pushes.

The `publication` branch is the latest publication history; `main` contains the
reviewed workflow, runner, and initial migration snapshot. Failed deployment commits remain
available for inspection. Deployment success requires a completed Pages run and
its matching receipt. Do not edit the exported snapshots as canonical notes.

## Rollback

The previous Quartz v4 site, its submodule, and its workflow remain in Git history
at `ae6d68d`. The workflow-only transition is `94f36bc`. Restore either into a
separate branch for review if rollback is needed; no history has been rewritten.

## Private engine repositories

Public Quartz engines use the workflow's normal GitHub token. For a private
engine in another repository, set the site repository's `EXOGRAPH_ENGINE_TOKEN`
Actions secret to a token with read access to that engine. The checkout uses this
optional token without persisting its credentials. The local publishing session
also needs GitHub CLI access to the selected site and engine repositories.
