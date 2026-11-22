# Contributing

This repository renders the GitHub profile for **Steve Andrew Rouse**. Small, focused changes are welcome — broken links, accessibility fixes, and asset improvements most of all.

## Ground rules

- **Keep status labels honest.** If a system is not shipped, do not describe it as shipped. Use *shipped*, *in development*, or *research*.
- **No invented metrics.** Stars, users, uptime and performance numbers belong in the README only when they can be reproduced.
- **One change per pull request.** A fix and a redesign in the same branch are two pull requests.

## Working on the README

1. The README is rendered inside GitHub's Markdown pipeline: no `<script>`, no external fonts, no `<style>` blocks.
2. Preview with a local Markdown renderer, then compare against the live profile page — GitHub strips attributes its sanitiser does not recognise.
3. Keep images served from this repository (`assets/`) or from stable public badge services.
4. All images need meaningful `alt` text, and decorative dividers use `alt=""`.

## Working on the animated assets

See [`docs/asset-notes.md`](docs/asset-notes.md) for the structure of `assets/hud.svg` and `assets/rain.svg`, and for the validation step to run before committing.

## Commit messages

Short imperative subject, optional body explaining why:

```
docs: fix dead Opera Nation link
docs: correct KATE.OS status to alpha
```

## Reporting security issues

Do not open a public issue — see [`SECURITY.md`](SECURITY.md).
