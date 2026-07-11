# HTM Apps Website

A static "studio" website (**HTM Apps**) for the How To Movie family of apps. It can be
hosted for free on GitHub Pages, Cloudflare Pages, Netlify, or any static host.

It starts with **How To Movie** (the rating-predictor app, live on the App Store) and
**How To TV** (coming soon); more HTM-family apps (Deal Hunter, Image Builder, Review
Writer) can be added later as extra cards on `index.html`.

## Pages

- `index.html`: studio landing page (the apps grid)
- `howtomovie2.html` / `how-to-tv.html`: per-app detail pages
- `howtomovie2-support.html` / `how-to-tv-support.html`: App Store support URL candidates
- `howtomovie2-privacy.html` / `how-to-tv-privacy.html`: App Store privacy policy URL candidates

(The `howtomovie2*` filenames are kept stable as URLs; the app is displayed as "How To Movie".)

## Notes

- Support currently routes to `thehowtomovie.com`; swap in a direct support email once chosen.
- If using a custom domain, add a `CNAME` file with that domain.

## Local Preview

From this folder's parent (`HTM Site`):

```sh
python3 -m http.server 8080 -d docs
```

Then open `http://localhost:8080`.

## Publishing

The site's source of truth is this `docs/` folder inside the monorepo. It is published to a
separate GitHub Pages repo with `publish-htm-site.sh` at the monorepo root:

```sh
./publish-htm-site.sh "commit message"   # sync + commit + push
./publish-htm-site.sh --check             # dry run, no push
```

The push step uses GitHub Desktop's credential (Claude's shell can't authenticate to
github.com); run the script to sync + commit, then click **Push** in GitHub Desktop.
