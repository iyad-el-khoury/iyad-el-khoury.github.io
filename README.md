# iyad-el-khoury.github.io

Source for my personal homepage, built with [Jekyll](https://jekyllrb.com/) and the [minima](https://github.com/jekyll/minima) theme (loaded via `remote_theme`, solarized-light skin).

## Structure

```
.
├── _config.yml       # site + theme configuration
├── _posts/           # blog posts (rendered under /blog/YYYY/MM/DD/title/)
├── index.md          # home page
├── about.md          # about page (shown in the nav bar)
├── Gemfile           # Ruby dependencies for local development
└── .gitignore
```

## Running locally

You'll need Ruby installed. Then, from this folder:

```bash
bundle install
bundle exec jekyll serve
```

The site will be available at http://localhost:4000. Live-reloads on file changes.

## Adding a new post

Add a file to `_posts/` named `YYYY-MM-DD-title.md` with front matter like:

```yaml
---
layout: post
title:  "My Post Title"
date:   2026-07-15 12:00:00 +0200
categories: general
---

Post content here.
```

## Adding a new page

Add a `.md` file at the root (like `about.md`) with:

```yaml
---
layout: page
title: My Page
permalink: /my-page/
---
```

To show it in the top navigation, add its filename to `header_pages` in `_config.yml`.

## Deploying to GitHub Pages

1. Create a repository named `iyad-el-khoury.github.io` (this exact name publishes it at the root domain).
2. Push this folder's contents to the `main` branch.
3. In the repo's **Settings → Pages**, set the source to the `main` branch (GitHub Pages supports `remote_theme` out of the box, no extra config needed).
4. Your site will build automatically and be live at https://iyad-el-khoury.github.io within a minute or two.

Any push to `main` afterwards will trigger a rebuild.
