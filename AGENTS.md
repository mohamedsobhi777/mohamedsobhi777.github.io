# Agent guidelines for Mohamed Sobhy's al-folio site

This is a personal site fork of [`alshedivat/al-folio`](https://github.com/alshedivat/al-folio). Read this file before editing. The site uses al-folio v1.x as a thin Jekyll starter; layouts, includes, Sass, Liquid tags, and runtime behavior live in versioned gems from [`al-org-dev`](https://github.com/al-org-dev).

## Where changes go

- Site identity, URL, and feature flags: `_config.yml`.
- Biography, publications, CV, contact details, projects, and assets: `_pages/`, `_bibliography/`, `_data/`, `_projects/`, and `assets/`.
- Dependency or plugin changes: keep `Gemfile` and the `_config.yml` plugin list aligned.
- Shared layouts, includes, Sass, tags, filters, and feature behavior: the owning gem. See [`docs/BOUNDARIES.md`](docs/BOUNDARIES.md) and [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md).

Do not create `_layouts/`, `_includes/`, `_sass/`, `_scripts/`, `assets/tailwind/`, `tailwind.config.js`, or `assets/webfonts/` here without an intentional site override. `npm run lint:style-contract` enforces the current no-override setup.

A feature may silently render nothing unless its gem is loaded, its flag is enabled, and its page opts in. Use `_config.yml` and the relevant page front matter together.

## Site URL and local commands

`_config.yml` sets `url: https://mohamedsobhi777.github.io` and an empty `baseurl`. Keep the empty baseurl for the domain-root user site. Build and serve from the repository root:

```bash
bundle install
npm ci
npm run lint:prettier
npm run lint:style-contract
bundle exec jekyll build
bundle exec al-folio upgrade audit --no-fail
bundle exec jekyll serve --host 127.0.0.1 --port 4000 --no-watch
```

The local preview is at `http://127.0.0.1:4000/`. `--no-watch` avoids duplicate-directory errors from `.codex/skills` and `.claude/skills` symlinks. Restart the server after edits.

The `main` branch holds source; `.github/workflows/deploy.yml` builds and publishes to `gh-pages`. Do not publish or push without the owner's approval. If local plugin-owned overrides are introduced, run `bundle exec al-folio upgrade overrides audit` and review `.al-folio-overrides.yml` before committing it.
