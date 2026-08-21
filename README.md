# khadushrohit.github.io

Design portfolio. Jekyll site, hosted free on GitHub Pages, edited through [Sveltia CMS](https://sveltiacms.app).

## Editing

Normal route: <https://khadushrohit.github.io/admin/> → sign in → edit. Saves commit to this repo and the site rebuilds in about a minute.

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
| `admin/` | Sveltia CMS interface and field config |
| `assets/css/main.css` | All styling, design tokens at the top |
| `assets/uploads/` | Images uploaded via the CMS |
