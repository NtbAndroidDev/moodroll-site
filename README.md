# moodroll-site

The public site for **Moodroll**, a photo mood journal for Android.

| Page | What Play points at it |
| --- | --- |
| https://ntbandroiddev.github.io/moodroll-site/ | store listing → **Website** |
| https://ntbandroiddev.github.io/moodroll-site/privacy/ | App content → **Privacy policy** |

Both are self-contained: no stylesheet, script, font or third-party request. `.nojekyll` makes Pages
serve the tree byte-for-byte rather than running Jekyll over it — which matters beyond styling, since
the policy's Markdown source carries an editorial comment and every renderer passes an HTML comment
straight into the page source of what is a legal document.

## ⚠️ This tree is generated. Do not edit it here.

It is built in the **app repository** (`moodroll`, private) and copied in whole:

```
moodroll/docs/index.md            ← the policy's source; this is what you edit and review
moodroll/tools/site/build_site.py ← the generator
moodroll/docs/site/               ← the output, copied here verbatim
```

To change anything on either page:

```bash
# in the app repo
python3 tools/site/build_site.py           # rebuild docs/site/
python3 tools/site/build_site.py --check   # verify it

# then here
cp -R ../moodroll/docs/site/. .
git commit -am "Update the site" && git push
```

An edit made directly in this repo is a change the app repo does not know about, and the next copy
silently reverts it.

Two things on the landing page are read out of the app itself at build time — the **mood palette**
and the **camera catalogue** — so they cannot drift from what the app actually ships. The generator
also refuses to build a page that names a real film brand, states a price or a trial length, claims
"no network permission", or says anything diagnostic. `moodroll/docs/PUBLISHING.md` §1 carries the
rest.

## Keeping the app's source out

This repo is public and the app repo is not. Nothing but the site belongs here.
