# AGENTS.md

Hugo personal blog. Theme (`themes/fortyten`) is a **git submodule** — it will be an empty directory after a plain clone.

## Setup (order matters)

```sh
git submodule update --init --recursive   # theme won't load without this
npm ci                                    # Tailwind CSS 4 deps used by the theme build
```

## Developer commands

```sh
hugo server            # local dev server
hugo                   # production build → public/
hugo --logLevel debug  # verbose build (matches CI)

hugo new content/posts/{year}/my-new-post.md  # create a new post
```

No npm scripts exist — invoke `hugo` directly.

## Toolchain constraints

- **Hugo extended** v0.152.2 is required (pinned in `.env`). The extended build is needed for Sass/SCSS in the theme. Wrong version or non-extended builds will fail.
- `npm ci` must run before `hugo` even though there are no npm scripts — the theme's Tailwind CSS 4 pipeline reads from `node_modules/`.

## Architecture

- All content lives in `content/posts/{year}/` as Markdown.
- `layouts/` holds site-level overrides only (currently just `404.html`).
- `static/_redirects` handles Netlify/Cloudflare Pages URL rewrites (strip `.html`, legacy `/categorias/` aliases).
- Home page outputs `HTML + RSS + JSON`; the JSON index powers the built-in site search — do not remove it from `hugo.yaml`.
- Each post sets its own `url:` slug in front matter rather than relying on Hugo's auto-slug.

## CI

- `.github/workflows/check-broken-links.yml` runs **on pull requests only** via `htmltest` on the built `public/` directory.
- Broken links are reported but don't fail the workflow (`continue-on-error: true`).
- Deployment is handled externally (Netlify/Cloudflare Pages Git integration) — no deploy workflow lives in this repo.
