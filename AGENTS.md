# Repository Guidelines

This document explains how to work on the 极客死亡计划 (Geek Death Project) repo as a contributor or tooling agent.

## Project Structure & Modules

- Hugo content lives in `content/` (posts, pages, drafts) and templates in `layouts/`.
- Static assets are in `static/`, generated CSS/JS under `assets/`, and i18n files in `i18n/`.
- Build-related scripts are in `scripts/`, with configuration in `config/`, `wrangler.toml`, and `pagefind.yml`.

## Build, Test, and Development

- `npm install` – install Node/UnoCSS dependencies locally.
- `npm run build:uno` – watch and rebuild UnoCSS for `layouts/` and `content/`.
- `npm run build:uno:prod` – generate production UnoCSS into `assets/css/uno.css`.
- `bash build.sh` – full production build: installs Hugo/Sass/Go, runs Go helpers, builds the site, and indexes search.
- There are no automated tests yet; `npm test` currently exits with an error placeholder.

## Coding Style & Naming

- Follow existing Hugo patterns: short, kebab-case filenames for templates (for example, `stats.html`, `home.html`).
- Use 2 spaces for indentation in HTML/Markdown, and idiomatic Go style (`go fmt`) for `.go` files in `scripts/`.
- Prefer English slugs, directory names, and Hugo keys; keep front matter consistent with existing content.

## Testing Guidelines

- Manually verify changes by running `bash build.sh` and checking the generated `public/` output locally.
- For Go helpers in `scripts/`, add small focused tests (if introduced) using the standard `testing` package and run with `go test ./scripts/...`.

## Commit & Pull Request Practices

- Use concise, descriptive commit messages (for example, `content: add post on X`, `layouts: tweak stats template`).
- Reference related issues in the description and include before/after screenshots for visual layout changes.
- Keep pull requests focused: group related content edits or feature work together, and avoid mixing refactors with content-only changes.

## Agent-Specific Notes

- When editing files, preserve existing front matter, shortcode usage, and partial includes.
- Do not change licenses or external configuration defaults (for example, Cloudflare Worker settings) without explicit instruction.
