# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This is a personal tax-focused blog published at `https://wrivestor.github.io` using Jekyll + GitHub Pages.

- **Title**: 최 회계사의 텍스노트 (Choi CPA's Tax Notes)
- **Theme**: `minima` (GitHub Pages supported)
- **Topic**: 세금 관련 이슈 및 실무 사례 (Korean-language tax commentary and case notes)

## Repository structure

```
.
├── _config.yml                       # Site metadata, theme, plugins, permalink format
├── index.md                          # Home page (uses minima's `home` layout → auto post list)
├── about.md                          # Static page at /about/
├── _posts/                           # Blog posts, filename YYYY-MM-DD-slug.md
│   └── 2026-10-08-welcome.md
└── README.md                         # One-line placeholder (not used by Jekyll)
```

Layouts, includes, and styles come from the `minima` gem; override by mirroring the gem's file paths (e.g. `_layouts/post.html`, `_includes/header.html`, `_sass/minima/custom-styles.scss`).

## Build and preview

GitHub Pages builds on push to `master` (takes ~1–2 min). No CI, no tests.

For local preview, add a `Gemfile`:

```ruby
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
gem "webrick"   # needed on Ruby 3+
```

Then:

```bash
bundle install
bundle exec jekyll serve --livereload   # http://localhost:4000
```

`_config.yml` changes require a restart; content changes hot-reload.

## Writing posts

- File path: `_posts/YYYY-MM-DD-slug.md` — the date in the filename determines the post date and must match the `date:` front matter.
- Required front matter:
  ```yaml
  ---
  layout: post
  title: "글 제목"
  date: 2026-10-08
  categories: [카테고리]
  tags: [태그1, 태그2]
  ---
  ```
- URL format is set in `_config.yml` as `/:year/:month/:day/:title/`.
- Future-dated posts are not published until their date arrives (unless `--future` is passed to `jekyll serve`).
- Draft posts go in `_drafts/` without a date in the filename, and only render with `jekyll serve --drafts`.

## Content conventions

- Posts are in Korean; keep that unless the user asks otherwise.
- Each post should carry a tax-advice disclaimer when it discusses specific scenarios — the `about.md` page carries the general disclaimer, but individual sensitive posts may need their own.
- Prefer categories like `공지`, `개정`, `사례`, `Q&A`, `메모` to match the planned taxonomy in the welcome post.

## Branching

Development happens on `claude/add-claude-documentation-e92FN`; `master` is the published branch. Push only to the branch you were instructed to use — a merge to `master` is what triggers publication.
