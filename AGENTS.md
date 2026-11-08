# Project guide

A Russian-language book. 
A minimal Hugo site without a theme framework or external fonts.

## Structure

- `content/_index.md`: introduction and authorship
- `content/toc.md`: table of contents
- `content/faxes/01.md` … `12.md`: flat chapter files, ordered by `weight`, not by their displayed fax numbers.
- `content/faxes/NN-commentary.md`: companion pages with `type = "commentary"`, excluded from the TOC. 
  Paired pages reference each other via `commentary` and `fax` front matter.
- `layouts/`: shared base, home, fax, commentary and TOC templates. 
- `layouts/partials/book-nav.html` provides header/footer previous / TOC / next links. 
  Commentaries use their fax's neighbors.
- `static/style.css`: all styling; other static files include images. 
- `public/` is generated output; do not edit or commit it.

## Decisions

- Font style: monospace for fax pages, regular font for commentaries.
  Preserve newlines, collapse spaces.
  Page theming: also monospace.
- Keep styling simple: warm-white paper on a dark background, centered fixed maximum width; full-width on mobile.
- Footer: don't push to the bottom, stick with the content.

## Commands and publishing

- `mise run build`: Run after template/config changes.
- GitHub Pages deploys via `.github/workflows/pages.yml` on pushes to `master`, using mise and the generated `public/` artifact.
