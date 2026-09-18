# HTM Apps Website (retired: redirects only)

**Since 2026-09-18 every page here is a redirect to its twin on
`thehowtomovie.com/apps/`.** Do not edit these pages on a release. The real
pages are built from `HTM Website/content/apps.json` by
`HTM Website/tools/build_app_pages.py`.

## Why it is still published

Every HTM app's App Store fields and in-app links point at thehowtomovie.com now,
but older installed builds (How to Movie 1.6 and earlier, Movie Canvas before its
link change) still open these URLs for support and privacy. Deleting the site
would break those links, and one of them is a privacy policy. A redirect keeps
them working and leaves nothing to maintain.

## What is here

| File | Status |
| --- | --- |
| `*.html` (16 pages) | Redirect stubs, written by `HTM Site/make_redirects.py`. Each keeps its canonical, its title and its `apple-itunes-app` banner tag |
| `assets/` | **Still load-bearing.** `ICON_DIR` for `HTM Website/tools/upload_media.py`, and the icon source for `HTM Marketing` |
| `styles.css` | **Still load-bearing.** The canonical `:root` brand tokens that ReelKit, the website theme and several app icon generators copy |
| `nextchapter-demo-library.csv` | **Still load-bearing.** Linked from Next Chapter's App Review notes |

Two page slugs differ from the app's name and the twin's slug: `howtomovie2` is
How to Movie (`/apps/how-to-movie/`), and `htm-image-builder` is Movie Canvas
(`/apps/movie-canvas/`).

## Changing a redirect

Each stub reads its target from its own `<link rel="canonical">`, so to point a
page somewhere else, change that tag and re-run:

```sh
python3 "HTM Site/make_redirects.py"           # report
python3 "HTM Site/make_redirects.py" --apply   # write (idempotent)
./publish-htm-site.sh "msg"                    # sync + commit; the push is the owner's
```

The script refuses a page with no canonical rather than guessing a target.
