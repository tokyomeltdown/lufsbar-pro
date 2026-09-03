# lufsbar-pro — landing page

The public page for **LUFSBar Pro**. Kept out of the product repository on
purpose: `tokyomeltdown/lufsbar-pro-app` is private and cannot serve Pages,
and the page has to be public. The same split caps REC uses.

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
| Repository | **`tokyomeltdown/lufsbar-pro`** (public) |
| Pages | live, from `main` / `docs` |
| URL | `https://tokyomeltdown.github.io/lufsbar-pro/` |

The name has a hyphen because `lufsbarpro` was taken when this repository was
created: GitHub compares names case-insensitively, and the private repository
was called `LUFSBarPro` at the time. It is `lufsbar-pro-app` now, so the short
name is free again — and staying free is all it will do. **Renaming this
repository would move the Pages URL, and GitHub does not redirect those.** The
page, the licence, the trial download and the Gumroad links all hang off
`/lufsbar-pro/`.

**This repository is public, so nothing that explains a decision goes in it.**
The Gumroad copy — the description, the post-purchase content, the refund
wording — lives in the private product repository, under `store/`,
along with the images and the script that renders them. Those files carry the
reasoning behind the wording as well as the wording, and reasoning about how a
refund term would hold up is not something a customer should find while
disputing one.

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

## Released

1.0 went out on 2026-09-02: Pages live, `v1.0` on Releases carrying
`LUFSBarPro.pkg`, and the Gumroad product published. The hub page links here.

