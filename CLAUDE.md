# lumaris-privacy

Public privacy-policy pages for every Lumaris app (HOST-01), GitHub Pages from `main`.
Personal ground rules: `~/personal/CLAUDE.md` (foundation). Remote: `git@github-personal:lumaris-apps/privacy.git` (ACC-05).

- One folder per app (`<app>/index.html`), listed on the root `index.html`. Spanish first, then English.
- A policy states only what the app's code does: re-read the app (database migrations,
  `app.config.ts`, dependencies, ADRs) before changing it, and update the "effective" date.
- No scripts, web fonts or third-party requests. Colours mirror Marea's palette in `style.css`.
- Never rename the repo, the org or a folder: Play holds these URLs.
- Hooks: `git config core.hooksPath .githooks` (pre-commit = ADR lint, pre-push = foundation guard).
