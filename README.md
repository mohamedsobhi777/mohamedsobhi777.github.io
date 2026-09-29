# Mohamed Sobhy's academic site

Source for the academic website intended for [mohamedsobhi777.github.io](https://mohamedsobhi777.github.io/). It is a fork of [al-folio](https://github.com/alshedivat/al-folio), with layouts and runtime supplied by the versioned al-folio gems.

## Content

- `_pages/about.md`: biography and research interests
- `_pages/publications.md`: publications
- `_pages/cv.md`: CV
- `_pages/contact.md` and `_data/socials.yml`: contact links
- `_projects/`: selected projects
- `_config.yml`: site identity, root URL, and feature settings

## Run locally

```bash
bundle install
npm ci
bundle exec jekyll serve --host 127.0.0.1 --port 4000 --no-watch
```

Open [localhost:4000](http://127.0.0.1:4000/). The server uses `--no-watch` because this checkout has agent-skill symlinks that Jekyll's watcher sees twice. Restart it after editing.

## Check and deploy

```bash
npm run lint:prettier
npm run lint:style-contract
bundle exec jekyll build
bundle exec al-folio upgrade audit --no-fail
```

The `main` branch holds source. The deploy workflow builds it and publishes `_site` to `gh-pages`; GitHub Pages must use the `gh-pages` branch as its source. `_config.yml` uses an empty `baseurl` because this is a user site served at the domain root.

For al-folio's underlying architecture and plugin boundaries, see [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) and [`docs/BOUNDARIES.md`](docs/BOUNDARIES.md).
