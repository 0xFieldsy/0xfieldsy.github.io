# AGENTS.md

Static GitHub Pages redirect site: a single `index.html` that meta-refreshes to `https://aef.me`.

## Layout

- `index.html` — the entire site. Edit the target URL in all four places (`<title>`, `http-equiv="refresh"`, `<link rel="canonical">`, `<a href>`) if it changes.
- `.github/workflows/build.yaml` — copies `index.html` into `dist` and deploys via GitHub Pages actions.

## Conventions

- No build tooling, dependencies, or tests. Keep it a single hand-written file.
- Deploy only happens on push to `main` (or a merged PR into `main`).

## References

- Astro's static redirect [template](https://raw.githubusercontent.com/withastro/astro/main/packages/astro/src/core/routing/3xx.ts): `noindex`, canonical link, and a fallback anchor.
