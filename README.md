# HTM Apps Website

A static "studio" website (**HTM Apps**) for the How to Movie family of apps. It can be
hosted for free on GitHub Pages, Cloudflare Pages, Netlify, or any static host.

Five apps have cards on `index.html`:

| App | Page slug | Status |
| --- | --- | --- |
| How to Movie | `howtomovie2` | Live on the App Store |
| How to TV | `how-to-tv` | Live on the App Store |
| Next Chapter | `nextchapter` | Coming soon |
| Movie Canvas | `htm-image-builder` | Live on the App Store |
| Deal Hunter | `deal-hunter` | Coming soon |

## Pages

Every app has three pages — `<slug>.html` (product), `<slug>-support.html` (App Store
support URL) and `<slug>-privacy.html` (App Store privacy policy URL) — plus
`index.html`, the studio landing page.

Two slugs deliberately differ from the display name and are kept stable as URLs:
`howtomovie2` is "How to Movie", and `htm-image-builder` is "Movie Canvas".

## Notes

- Support routes to `thehowtomovie.com`, with two exceptions. The Next Chapter pages use
  the `support.altaaffirmations@gmail.com` inbox shared with the other two studio sites.
  The Deal Hunter pages use `htm.dealhunter@gmail.com`, an inbox of its own — it is
  per-app, not the shared address, so do not reuse it for another app. Both the support
  and privacy pages carry it, and the canonical WordPress copies must be changed to match
  (`support_email` on the app's entry in `HTM Website/content/apps.json`).
- Coming-soon pages carry a placeholder button; swap in the real App Store link at launch.
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
