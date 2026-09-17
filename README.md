# goatham-site

Promotional site for [GoatHam](https://play.google.com/store/apps/details?id=com.jcalado.goatham),
a field companion for the outdoor amateur radio programmes. The app itself lives
in the `ontheapp` repository.

Static, no build step. Open `index.html`, or serve the directory:

```sh
python3 -m http.server 8000
```

## Files

| Path | What it is |
|---|---|
| `index.html` | The whole page. One file, no framework. |
| `styles.css` | Every style. Tokens at the top, sections in page order. |
| `PRODUCT.md` | Who this is for, the brand, what it must not look like. |
| `DESIGN.md` | The visual system, and why each value is what it is. |
| `assets/` | Artwork and screenshots, all generated (see below). |

## Assets

Nothing in `assets/` is hand-made. Everything derives from two sources in the
app repository, so a change there is re-exported rather than redrawn:

- `design/brand/app_icon.png` gives `ridge.png` (the hero band, cropped to keep
  the sun and the goat's horns in shot), `scene.png`, `og.png` and the icons.
  The artwork's sky is the same cream as the page ground, which is why the hero
  band needs no mask or fade to sit on the page.
- `dist/screenshots/` gives `shot-spots`, `shot-field` and `shot-map`, resized
  to 660px wide and saved as progressive JPEG.

## Known gaps

- **The screenshots are in Portuguese.** They were captured from a pt-PT device.
  They demonstrate that the app ships two languages, but English captures would
  suit an English page better.
- **They also predate the rename**, so they show the older green interface
  rather than anything matching the icon's palette. The device frames are navy
  precisely so the app's green reads as product rather than as brand colour.
- **The Play link 404s until the listing exists.** The URL is built from the
  package name, `com.jcalado.goatham`, so it will resolve the moment the app is
  published. The APK link points at this repository's releases.

## Licence and attribution

The map screenshot shows OpenStreetMap tiles, so the footer carries the
attribution. Keep it there if the screenshots change.
