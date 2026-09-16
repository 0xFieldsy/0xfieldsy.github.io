# AGENTS.md

Static GitHub Pages redirect site: a single `index.html` that meta-refreshes to `https://aef.me`.

## Layout

- `index.html` — the entire site. Page is blank except a shadcn-style spinner (inline CSS, Lucide `loader-circle`). The `<title>` mirrors the production `aef.me` home title and is kept in sync manually. Edit the target URL in two places (`http-equiv="refresh"` and `<link rel="canonical">`) if it changes.
- `.github/workflows/build.yaml` — copies `index.html` into `dist` and deploys via GitHub Pages actions.

## Favicon

- `favicon.ico` is the source icon from `aef.me`; `index.html` embeds it as an inline `data:image/png;base64,...` `<link rel="icon">`.
- The icon is pure black and alpha, so it re-encodes losslessly as a PNG. To regenerate: `uv run --with pillow --with zopfli python ...`, converting `favicon.ico` to `LA`, filtering with `None`, and zopfli-compressing the IDAT.

## Conventions

- No build tooling, dependencies, or tests. Keep it a single hand-written file.
- Deploy only happens on push to `main` (or a merged PR into `main`).

## References

- Astro's static redirect [template](https://raw.githubusercontent.com/withastro/astro/main/packages/astro/src/core/routing/3xx.ts).
