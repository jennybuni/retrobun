# Repository Guidelines

## Project Structure & Module Organization
- `content/posts/<slug>/` holds Hugo page bundles (`index.md` plus local media) so links stay stable.
- `static/` serves global assets verbatim; avoid duplicating bundle media to prevent stale copies.
- `archetypes/default.md` seeds `hugo new`; update required fields and switch to YAML (`---`) if drafts should match published posts.
- `themes/re-terminal/` is a git submodule; run `git submodule update --init --recursive` after cloning and put custom layouts in top-level `layouts/`.
- `public/` and `resources/_gen/` are disposable build artefacts—clean or rebuild them instead of editing manually.

## Build, Test, and Development Commands
- `hugo server -D` starts the draft-enabled dev server; watch console warnings for broken links or missing params.
- `hugo --minify --destination public` builds the production bundle published by GitHub Pages.
- `hugo new posts/<slug>/index.md` scaffolds a draft bundle; use a kebab-case slug and update front matter before publishing.

## Coding Style & Naming Conventions
- Prefer YAML front matter wrapped in `---`; keep `tags`/`categories` inline and quote strings with punctuation.
- Use sentence case for titles, wrap lines near 100 characters, and keep emoji to intro blurbs only.
- Name media in kebab-case (e.g., `fake-cart-closeup.jpg`), provide descriptive alt text, and store assets beside their bundle.
- Run `hugo server` before staging to catch warnings, and never commit `.hugo_build.lock`, `public/`, or `resources/_gen/`.

## Testing Guidelines
- `hugo --printPathWarnings --printUnusedTemplates` flags missing assets, unused layouts, and taxonomy issues pre-review.
- Manually test `http://localhost:1313` for navigation, banner behaviour, responsive layout, and image clarity.
- Keep new binaries under 1 MB and compress large screenshots to maintain quick builds and loads.

## Commit & Pull Request Guidelines
- Write imperative commits such as `Add fake NES cart checklist` instead of generic "updates".
- Group related content, asset, and config changes, isolating theme submodule bumps when needed.
- Open PRs with a concise summary, preview link or screenshot, and notes on affected menus or taxonomies; link issues when available.
- Request review before merging theme or configuration changes so shared layouts stay stable for other authors.
