# HOST-01 — Privacy policies are static pages on GitHub Pages

- **Status:** Accepted
- **Date:** 2026-11-25
- **Builds on:** foundation:ACC-05

## Context

Google Play requires a public privacy policy URL (a web page, not a PDF) for every health
app, and for most others. Lumaris apps have no backend and no website. The policy must be
free to host, versioned (every change on public record), and kept apart from the app repos,
which are private.

Options weighed:

| Option | Rejected because |
|---|---|
| Pages inside each app repo | App repos are private; free Pages needs a public repo. Making an app public just for this isn't worth it. |
| Expo web + EAS Hosting | Turns the app into a web app (SQLCipher, Keystore and the biometric lock are phone-only), and a typo fix would go through an app web deploy. |
| Google Sites or a gist | No proper history; less clean. |
| A custom domain | Costs money and renewals; nothing needs it yet (YAGNI). Can sit on top of Pages later. |

## Decision

- One public repo, **`lumaris-apps/privacy`**, served by GitHub Pages from `main` (root).
  Under the organization so the address shows the studio, not the username (ACC-05).
- One folder per app (`marea/index.html` → `lumaris-apps.github.io/privacy/marea/`), and a
  root page listing every app. Plain HTML and one stylesheet: no build, no framework,
  `.nojekyll` so files are served as written.
- Spanish first, then English, on the same page, like the apps.
- The page makes no request to any other site (system fonts, no scripts, no analytics).
- Each policy is written from the app's code and ADRs, and is updated in the same week any
  change to the app alters what it does with data.

## Consequences

- Free, and the commit history is the public record of every policy version.
- The URL never changes once given to Play; renaming the repo or the organization would break
  it, so neither is renamed.
- A new app = a new folder and a line on the root page.
