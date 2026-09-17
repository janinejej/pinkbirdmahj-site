# Card-purchase wording

**Changed:** 8 September 2026
**Scope:** five places across `index.html`, `support.html`, `privacy.html`

## What changed

**Before**

> An official National Mah Jongg League card is required to play, and must be
> purchased from **the League**.

**After**

> An official National Mah Jongg League card is required to play, and must be
> purchased from **the League, an authorized store, or a dealer**.

## Why

The original wording implied the League was the only place to buy a card. Cards are
also sold through authorized retailers, so the old sentence was narrower than the
facts. It appeared on every page, including inside the NMJL disclaimer, where being
precise matters most.

## Where it appears

| Page | Location |
|---|---|
| `index.html` | "You bring the card" section, body paragraph |
| `index.html` | footer NMJL disclaimer (`p.legal`) |
| `support.html` | FAQ — *Do I need a National Mah Jongg League card?* |
| `support.html` | footer NMJL disclaimer |
| `privacy.html` | footer NMJL disclaimer |

All five were changed together. If this sentence is ever revised again, revise all
five — a site that says two different things about where to buy a card is worse than
one that says the wrong thing consistently.

## Wording note

An intermediate version read "…from the League or an authorized store or dealer".
That was replaced because the doubled *or … or* read awkwardly; the comma series is
the same claim, more cleanly. No change in meaning between those two.

## Watch item

This slightly softens the disclaimer. The old text pointed at the League as sole
source; the new text acknowledges a reseller channel. It still disclaims affiliation
with the NMJL in the same terms. **If Lloyd & Mousilli supply specific language for
that paragraph, theirs supersedes this** — see the `legal/` folder in the app repo.

## To revert

The change is confined to that one sentence in the five locations above; no markup,
styling, or surrounding copy was touched.
