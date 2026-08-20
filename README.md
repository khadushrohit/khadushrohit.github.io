# khadush.com

Jekyll site, hosted free on GitHub Pages, edited through [Pages CMS](https://pagescms.org).

## Editing

Normal route: pagescms.org → sign in with GitHub → pick this repo. Write, hit save, the site rebuilds in about a minute.

Manual route: posts are Markdown files in `_posts/`, named `YYYY-MM-DD-slug.md`. The slug becomes the URL.

## Local preview

```bash
bundle install
bundle exec jekyll serve
```

## Structure

| Path | What it is |
|---|---|
| `_posts/` | Blog posts |
| `_projects/` | Portfolio case studies |
| `_layouts/` | Page templates |
| `assets/css/main.css` | All styling, tokens at the top |
| `assets/uploads/` | Images uploaded via Pages CMS |
| `.pages.yml` | Pages CMS field config |
