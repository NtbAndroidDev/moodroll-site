# moodroll-site

The public home of **Moodroll's privacy policy** — the URL Google Play links to from the store
listing and from App content → Privacy policy.

- **Live page:** https://ntbandroiddev.github.io/moodroll-site/
- One file, `index.html`, self-contained: no stylesheet, no script, no font and no image is fetched
  from anywhere. It renders the same from a static host, from a `file://` URL, and on a printer.
- `.nojekyll` tells GitHub Pages to serve it byte-for-byte rather than running Jekyll over it.

## ⚠️ `index.html` is generated. Do not edit it here.

It is built in the **app repository** (`moodroll`, private) and copied in:

```
moodroll/docs/index.md                  ← the source; this is what you edit and review
moodroll/tools/policy/build_policy.py   ← the generator
moodroll/docs/index.html                ← the output, copied here verbatim
```

To change a word on the page:

```bash
# in the app repo
$EDITOR docs/index.md
python3 tools/policy/build_policy.py          # rewrites docs/index.html
python3 tools/policy/build_policy.py --check  # and verifies it

# then here
cp ../moodroll/docs/index.html index.html
git commit -am "Update the privacy policy" && git push
```

An edit made directly in this repo is a change the app repo does not know about, and the next copy
silently reverts it. `moodroll/docs/PUBLISHING.md` §1 carries the rest: what makes the page false,
and why the Markdown is not published in its place.

## Keeping the app's source out

This repo is public and the app repo is not. Nothing but the policy page belongs here.
