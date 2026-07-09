# probeadd.github.io

Personal site + blog. Custom monochrome Jekyll theme (no stock theme).

- **Homepage** — centered profile, links, and the **5 newest posts**.
- **Archive** (`/posts/`) — all posts, grouped by year, **10 per page** (auto-paginated).

## Requirements

- **Ruby 3.3.11** — pinned in `.ruby-version`, managed with [rbenv].
  The macOS system Ruby (2.6) **will not work** (bundler errors out).
- One-time dependency install:

  ```sh
  bundle install
  ```

If `bundle` complains about `bundler 2.5.22` / Ruby 2.6, rbenv is not active in
your shell. Make sure its shims are on your `PATH` (`rbenv init`) so `ruby -v`
reports 3.3.11, then retry.

## Run locally

```sh
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>. With `--livereload` the browser refreshes
automatically when you save a post or edit styles.

> Editing `_config.yml` is **not** hot-reloaded — stop and restart `serve` for
> those changes to take effect.

## Build (no server)

```sh
bundle exec jekyll build      # outputs the static site to _site/
```

## Add a post

Create a file in `_posts/` named `YYYY-MM-DD-my-title.md`. The date must be
valid, and the `my-title` slug becomes the URL (`permalink: /posts/:title/`).

```markdown
---
layout: post
title: "My Post Title"
date: 2026-07-10
tags: [optional, tags]
---

Body in Markdown.

LaTeX renders via MathJax: inline \( a^2 + b^2 = c^2 \) and display \[ E = mc^2 \].
```

That's it — the newest post shows up automatically on the homepage and Archive;
there is no index to update by hand. See `_posts/2026-07-09-hello-world.md` for a
full example.

## How the pages behave

- Homepage post count is capped at 5 (`limit: 5` in `index.html`).
- The Archive paginates at 10 posts per page (`paginate: 10` in `_config.yml`).
  Extra pages (`/posts/page2/`, …) and the Newer/Older nav appear automatically
  once there are more than 10 posts. Change `paginate` to adjust, then restart
  the server.

## Deploy

Push to `main` — GitHub Pages builds and publishes the site. It runs the
`github-pages` gem in safe mode, so only whitelisted plugins work. Pagination
uses **`jekyll-paginate` (v1)**; `jekyll-paginate-v2` is **not** supported there.

[rbenv]: https://github.com/rbenv/rbenv
