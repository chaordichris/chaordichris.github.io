# Agent Guide

## Repository Shape

- This is a single-site Jekyll repository; the Beautiful Jekyll theme is vendored in `_layouts/`, `_includes/`, `assets/`, and supporting root files.
- Site content lives in root Markdown/HTML pages and `_posts/`; site-wide settings and navigation are in `_config.yml`.
- A templated page must have YAML front matter, including the opening and closing `---`; `index.html` uses the `home` layout.
- Blog posts must be named `YYYY-MM-DD-title.md` so Jekyll recognizes and dates them correctly.
- `_site/` and `Gemfile.lock` are intentionally ignored; do not commit generated output or a dependency lockfile.

## Development

- Dependencies are Ruby gems declared by `beautiful-jekyll-theme.gemspec` through `Gemfile`; the theme requires Jekyll `~> 3.8`.
- Install dependencies with `bundle install`, then run locally with `bundle exec jekyll serve --future`.
- Build locally with `bundle exec jekyll build --future`; there is no separate test, lint, or typecheck configuration.
- CI's authoritative check is a Jekyll 3.8 Docker build with `jekyll build --future` (see `.github/workflows/ci.yml`); currently both it and local Ruby 2.6 can fail resolving unpinned `ffi` because the latest release requires Ruby 3+, so do not add the ignored lockfile as a workaround.

## Change Boundaries

- Edit root pages and `_posts/` for published content; edit `_config.yml` for navigation, metadata, URLs, and theme settings.
- Edit `_layouts/`, `_includes/`, `assets/css/`, or `assets/js/` only for shared presentation or behavior changes, since those files affect the whole site.
- Keep image and other static asset paths consistent with the `/assets/...` paths used by front matter and `_config.yml`.
