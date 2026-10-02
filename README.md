# CV

A CV site in English and Italian: Jekyll on GitHub Pages, with a PDF and a
Markdown export rebuilt on every change.

## Edit it

**Everything you write is in [`_data/cv.yml`](_data/cv.yml)** (English) and
[`_data/cv_it.yml`](_data/cv_it.yml) (Italian) — change one, change the other.
On github.com: open the file → pencil icon → edit → **Commit changes**. The
workflow rebuilds the pages, `cv.pdf` and `cv.md` in a minute or two (Actions
tab shows progress). Fields you leave out disappear from the page; text accepts
Markdown.

Headings and button labels are in [`_data/ui.yml`](_data/ui.yml).

## What visitors get

| | |
|---|---|
| the page | `https://<username>.github.io/`, Italian at `/it/` — phone-friendly |
| **Theme** | light / dark / black; follows the system at first, then remembers |
| **Design** | Atlas (default), Editorial, Bento, Sidebar — same content, different layout |
| **Download PDF** | `cv.pdf` and `it/cv.pdf`, rendered by headless Chrome from the print stylesheet on every build |
| **Markdown** | `cv.md` and `it/cv.md`, for pasting into forms and emails |
| **Print** | the browser's own print / Save as PDF — same stylesheet as the PDF |

`?theme=black` and `?design=editorial` on the URL link straight to a variant.

## Preview locally (no Ruby needed — Docker)

```bash
docker run --rm -it -p 4000:4000 -v "$PWD:/srv/jekyll" -w /srv/jekyll \
  ruby:3.3 sh -c "bundle install && bundle exec jekyll serve --host 0.0.0.0 --livereload"
```

Then open http://localhost:4000. Edits to `cv.yml` reload the page.

## One-time setup on GitHub

1. Create the repo `<username>.github.io` (public), push this directory.
2. **Settings → Pages → Source: GitHub Actions.**
3. Set `url:` in `_config.yml` to `https://<username>.github.io`.

## Files

| file | what |
|---|---|
| `_data/cv.yml`, `_data/cv_it.yml` | the content — the files you normally touch |
| `_data/ui.yml` | headings and button labels, per language |
| `_includes/cv-page.html` | the page template, shared by `index.html` and `it/index.html` |
| `_includes/cv-md.html` | the Markdown export template (published as `/cv.md`, `/it/cv.md`) |
| `_includes/map-land.svg` | the coastline for the Places map (Natural Earth, public domain) |
| `_layouts/default.html` | `<head>`: link preview, search-engine data, theme/design start-up |
| `assets/css/cv.css` | themes, the four designs, and print/PDF styles |
| `assets/img/og.png` | the image shown when the link is pasted into LinkedIn, WhatsApp… |
| `.github/workflows/pages.yml` | build → PDFs → publish |

The map plots `places:` from the content file; a new place inside Europe only
needs its longitude and latitude.
