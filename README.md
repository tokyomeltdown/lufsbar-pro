# lufsbar-pro — landing page

The public page for **LUFSBar Pro**. Kept out of the product repository on
purpose: `tokyomeltdown/LUFSBarPro` is private and cannot serve Pages, and the
page has to be public. The same split caps REC uses.

```
docs/
├── index.html        the page
├── icon.png          the app icon, 512×512
├── og-image.png      the social card, 1200×630 — generated, see below
└── eula/index.html   the published licence

og-source.html        what og-image.png is rendered from
make-og.sh            renders it
```

## Regenerating the social card

`docs/og-image.png` is not drawn by hand. Edit `og-source.html` and run:

```bash
bash make-og.sh
```

It renders through headless Chrome at exactly 1200×630, which is what the
cards crop to; a card that is off by a pixel gets rescaled and the type goes
soft. Keeping it generated means it follows the page's colours instead of
drifting from them.

## Where it goes

| | |
|---|---|
| Repository | **`tokyomeltdown/lufsbar-pro`** (public) — **not yet created** |
| Pages | serve from `main` / `docs` |
| URL | `https://tokyomeltdown.github.io/lufsbar-pro/` |

`lufsbarpro` cannot be used as the repository name: GitHub treats names
case-insensitively and it collides with the private `LUFSBarPro`.

**Do not create the repository until the page is finished.** An empty public
repository under that name announces an unreleased product.

## Links the page depends on

| Link | Target |
|---|---|
| Buy | `https://tokyomeltdown.gumroad.com/l/lufsbarpro` |
| Trial download | `https://github.com/tokyomeltdown/lufsbar-pro/releases/latest/download/LUFSBarPro.pkg` |
| Free version | `https://tokyomeltdown.github.io/LUFSBar/` |

**The download link points at this repository's own Releases**, so the package
has to be uploaded here rather than to the private one. The file name has no
version in it, the same rule caps REC follows, because the link is fixed.

## House style

- **Paid products are black, free ones are white.** The free LUFSBar page is
  the light sibling of this one.
- Language switching follows caps REC: one `lang-en` / `lang-ja` class on
  `<body>`, every string present twice as `.en` / `.ja`. The first visit
  follows the browser's language; after that the choice is remembered.
- No external requests. The panel in the hero is drawn in HTML rather than
  screenshotted, so there is nothing to load and nothing to re-shoot when the
  app's colours change.

## Preview

```bash
python3 -m http.server 8731 --directory docs
```

## Before publishing

- [x] A real Open Graph image — `og-image.png`, 1200×630.
- [ ] The Gumroad product page itself — description, cover, and a link to the
      licence, so the terms are readable **before** purchase. §12 of the EULA
      says sales are final, and that is only fair if the buyer could read it.
- [ ] Check the trial download link once the package is actually on Releases.
