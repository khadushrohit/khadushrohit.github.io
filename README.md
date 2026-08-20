# khadush.com

Design portfolio. Jekyll site, hosted free on GitHub Pages, edited through [Pages CMS](https://pagescms.org).

## Editing

Normal route: pagescms.org → sign in with GitHub → pick this repo. Write, hit save, the site rebuilds in about a minute.

Manual route: case studies are Markdown files in `_projects/`. The filename becomes the URL.

## Local preview

```bash
bundle install
bundle exec jekyll serve
```

## Structure

| Path | What it is |
|---|---|
| `_projects/` | Portfolio case studies |
| `_layouts/` | Page templates |
| `assets/css/main.css` | All styling, tokens at the top |
| `assets/uploads/` | Images uploaded via Pages CMS |
| `.pages.yml` | Pages CMS field config |
