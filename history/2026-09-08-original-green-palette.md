# Original green palette

**In use:** 3 September 2026 (site launch) → 8 September 2026
**Replaced by:** navy `#2A5298` / muted gold `#C8A96A` / soft ivory `#FAF6EC`
**Reason for change:** the green read as a generic mahjong-felt colour and shared
nothing with the Pink Bird Mahj identity. Navy + gold + ivory reads as a
teaching brand rather than a card table, and the pink bird carries the warmth.

Screenshots of the pages as they looked on this palette:
`2026-09-08-before-index.png`, `-support.png`, `-privacy.png`.

---

## The palette

Declared identically in the `:root` of all three pages
(`index.html`, `support.html`, `privacy.html`).

| Variable | Hex | Role |
|---|---|---|
| `--green` | `#1A472A` | header bar, footer bar, `h2` headings, `.card h3` |
| `--green-soft` | `#2E7D32` | 4px left border on `.note` (index) and `.callout` (privacy); declared but unused on support |
| `--pink` | `#C2185B` | all body links, the hero tagline "DRILLS, NOT LESSONS" |
| `--pink-soft` | `#E91E63` | declared on `index.html` only; never actually used |
| `--cream` | `#F7F3EC` | page background |
| `--ink` | `#1E1B18` | primary body text |
| `--muted` | `#5C554D` | secondary text — lead paragraph, card copy, captions |
| `--rule` | `#E2DACE` | hairline borders and section dividers |

## Colours hardcoded outside `:root`

These were literal hex values in the rules, not variables — easy to miss on a revert.

| Hex | Where |
|---|---|
| `#F8BBD0` | pale pink — the `: Card Coach` half of the logo (`.brand span`), and footer links |
| `#D7E8DC` | pale green — header nav links |
| `#C9DDD0` | pale green — footer body text |
| `#9DBCA8` | muted green — the footer legal/disclaimer paragraph |
| `#fff` | card, note, callout and contact-box backgrounds; header and footer text |

## Notes on how it was built

- Every page carried its own complete copy of the CSS in a `<style>` block.
  There was no shared stylesheet, so any palette change had to be made three times.
- `index.html` wrote the `:root` block one variable per line; `support.html` and
  `privacy.html` packed it onto two lines. Same values, different formatting.
- The header and the footer used the *same* green (`--green`), so the two bands
  were identical rather than tonally related.
- `.card`, `.note`, `.callout` and `.contact` all used a plain `#fff` background
  against the `#F7F3EC` cream — a difference of about 3%, so the boxes barely
  separated from the page.
- The mascot artwork was never restyled and is unaffected by any of this:
  `pink-bird-branch.png`, `coach-starling.png`, `coach-starling-branch.png`,
  `one-bam-original.jpg`.

## To revert

The change was confined to the `<style>` block of the three HTML files; no markup,
copy, image or file name changed. Either:

- `git checkout <commit-before-the-palette-change> -- index.html support.html privacy.html`, or
- paste the `:root` table above back over the current one and restore the four
  hardcoded pale-green/pink values listed in the second table.
