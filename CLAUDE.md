# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This is a GitHub Pages site published at `https://wrivestor.github.io`. It is a Jekyll project that currently contains no custom content — only `_config.yml` (sets `theme: jekyll-theme-minimal`) and a one-line `README.md`. All layouts, styles, and default pages come from the [`jekyll-theme-minimal`](https://github.com/pages-themes/minimal) gem provided by GitHub Pages.

Because there is no `Gemfile`, no `_layouts/`, no `_includes/`, no `_posts/`, and no top-level `index.md`/`index.html`, the live site renders using the theme's defaults plus `README.md` as the index page (GitHub Pages fallback behavior).

## Build and preview

GitHub Pages builds the site automatically on push to the default branch (`master`). There is no CI or test suite in this repo.

For local preview, a `Gemfile` must be added first (it does not currently exist):

```ruby
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
```

Then:

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000
```

## Conventions when adding content

- **Pages**: add `index.md` (or other `.md`/`.html` files) at the repo root with YAML front matter (`---\nlayout: default\ntitle: ...\n---`). Once `index.md` exists, it replaces `README.md` as the rendered home page.
- **Posts**: place in `_posts/` named `YYYY-MM-DD-title.md` with front matter.
- **Theme overrides**: to override the theme, mirror the file path from the `jekyll-theme-minimal` gem (e.g. create `_layouts/default.html`, `_includes/head.html`, or `assets/css/style.scss`).
- **Config changes** in `_config.yml` are only picked up on Jekyll restart, not on file watch.

## Branching

Active development happens on `claude/add-claude-documentation-e92FN`; `master` is the published branch. Push only to the branch you were instructed to use.
