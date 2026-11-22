# Animated asset notes

Both banners are hand-authored SVG. They animate with SMIL (`<animate>`, `<animateTransform>`) only, because GitHub strips `<script>` from README content and blocks external fonts. That means they work in GitHub's own renderer and in any static Markdown preview, with no build step.

## `assets/hud.svg` — HUD banner

1,024 × 240. Layered back to front:

| Layer | Id / selector | Purpose |
| --- | --- | --- |
| Background wash | `.bg` | near-black base with a soft green radial glow |
| Matrix columns | `.col` | falling glyph strips, staggered `begin` offsets |
| Scanline | `.scan` | single bright bar sweeping top to bottom |
| Corner brackets | `.frame` | the four registration marks |
| Title | `.title` | glitch pairs offset by a few milliseconds |
| Readouts | `.ro` | mode, uptime and register counts in the lower band |
| K ring | `.ring` | rotating concentric ring on the right |

To retime the effect, change the `dur` and `begin` values in the matrix column groups. To recolour, change `--ink` equivalents inline — GitHub ignores CSS custom properties in SVG, so colours are literal `#00ff41` style values.

## `assets/rain.svg` — divider

Full-width, 90 px tall, 18 staggered streams. Used between README sections as a decorative rule (`alt=""` so screen readers skip it). Keep it under roughly 6 KB: it renders on every profile visit and is served raw from `raw.githubusercontent.com`.

## Before committing

Both files must parse as XML. From the repository root:

```bash
python -c "import xml.etree.ElementTree as ET; [ET.parse(p) for p in ('assets/hud.svg','assets/rain.svg')]; print('ok')"
```

A malformed file renders as a broken-image icon on the profile, which is why the check is in the pull request template.

## Constraints worth remembering

- No `<script>`, no external `<link>`, no web fonts.
- No `<foreignObject>` — GitHub's sanitiser strips it.
- Keep `viewBox` and drop fixed `width`/`height` where the image should scale.
- Gradients need unique `id`s per file; duplicated ids leak between inline SVGs.

## Fallback

The README links these by absolute `raw.githubusercontent.com` URL, so a rename or a move to another directory breaks the banner until every reference is updated. If a banner ever fails to render, check that URL first.
