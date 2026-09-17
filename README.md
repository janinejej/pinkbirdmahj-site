# pinkbirdmahj.com — the company website

Three static pages, no build step, no dependencies. Everything is inline; there is nothing to
install and nothing to compile.

```
index.html      what the app is, the drills, the company
privacy.html    privacy policy  — REQUIRED by both stores before submission
support.html    support + FAQ   — REQUIRED by the App Store before submission
img/
  pink-bird-branch.png         mascot on a bamboo branch — hero + favicon
  coach-starling.png           the bird with binoculars — Coach Starling
  coach-starling-branch.png    binoculars version on the branch (not used on the
                               site yet; kept here for store listings and social)
  one-bam-original.jpg         the original painting, EXIF stripped, resized to 900px
```

All paths are **relative**, so you can double-click `index.html` and preview the whole site
locally exactly as it will appear once deployed. Rendered and checked at 1200px and 390px.

## Why this exists now

Apple's organization enrolment requires a website:

> "Your organization's website must be publicly available and functional, and its domain name must be
> associated with your organization. Links to social media webpages or websites that contain minimal
> content or display a message from a domain registrar won't be accepted."

A parked page or "coming soon" placeholder fails that check. But the site is not a detour — the App
Store requires a **privacy policy URL** *and* a **support URL** to submit, and Google Play requires a
privacy policy URL. One piece of work clears the enrolment blocker and two launch requirements.

## Deploying — domain is registered at Porkbun

Keep the registration at Porkbun; only the DNS records change.

### GitHub Pages, from the `pinkbirdmahj-site` repo

The site lives in its **own public repo**: `github.com/janinejej/pinkbirdmahj-site`, served by GitHub
Pages from that repo's **root**. Clone it to `...\Program\pinkbirdmahj-site` and edit it there.

**Why it is not in the app repo.** Pages cannot serve a private repo without a paid plan, and
`pink-bird-mahj` must stay private: it holds the full NMJL pattern compilation, the legal analysis
and fair-use position, pricing and licensing negotiating positions, and the launch blockers. None of
that should be public. The site is four HTML files and four images with nothing sensitive in them,
so it gets its own repo rather than forcing the app repo open.

1. Repo → **Settings → Pages** → Source: *Deploy from a branch* → branch `main`, folder
   **`/ (root)`**.
2. Same page, **Custom domain**: `pinkbirdmahj.com` → Save. GitHub commits a `CNAME` file to the
   repo — leave it, and `git pull` before your next local commit so you do not conflict with it.
3. In **Porkbun's DNS editor**, add exactly these five records:

   | Type | Host | Value |
   | --- | --- | --- |
   | A | `@` | `185.199.108.153` |
   | A | `@` | `185.199.109.153` |
   | A | `@` | `185.199.110.153` |
   | A | `@` | `185.199.111.153` |
   | CNAME | `www` | `janinejej.github.io` |

   (IPs from GitHub's own docs, checked 3 Sep 2026. Re-check at `docs.github.com` if you are setting
   this up much later — they have changed before.)
4. Wait 15 minutes to an hour for DNS, then back in Settings → Pages tick **Enforce HTTPS** once the
   certificate has been issued.

🔴 **Leave the MX records alone.** Add only the five records above. Business email
(`janinejej@pinkbirdmahj.com`, `info@`) rides on the MX records; breaking them mid-enrolment means
missing Apple's mail.

`.nojekyll` turns off GitHub's Jekyll processing — we serve plain HTML and want the files published
exactly as written.

### Cloudflare Pages — better later, riskier today

Cleaner long-term: the scan proxy is going to be a Cloudflare Worker, and with the domain on
Cloudflare that Worker can answer on `scan.pinkbirdmahj.com` instead of a `workers.dev` subdomain.

The catch is that it wants the domain's **nameservers** moved to Cloudflare, which moves *all* DNS
including MX. Cloudflare imports existing records automatically, but a mistake takes business email
down — mid-enrolment, with Apple mailing us. **Do this after enrolment clears, not before**, and
verify MX records match Porkbun's exactly before flipping the nameservers.

## Before Apple reviews it

- [ ] All three pages load over **https** at the apex domain.
- [ ] "Pink Bird Mahj LLC" appears and matches the D-U-N-S record exactly (D-U-N-S 147771702).
- [ ] `info@pinkbirdmahj.com` receives mail.
- [ ] No placeholder text, no lorem ipsum, no dead links.

## Worth adding when there is something to add

**App screenshots.** The artwork is in, which already puts this well clear of "minimal content",
but real screenshots of The Practice Table would sell it better than the drill cards do. Store
listings need screenshots anyway, so they are not wasted work.

## Settled: the artist is not named until she decides, as an adult

The origin story credits "my niece" and does **not** name her. This is no longer an open
question — it was decided on 17 September 2026 and it is now a contractual obligation, not a
preference.

**The rule:** the credit is unconditional and permanent; her *name* is withheld while she is a
minor. After she turns 18 she may elect, in writing, to be credited by name — and may withdraw
that election later, at any time, without giving a reason. Nobody is to ask her for that election
before she is 18.

**Why.** She was a child when she painted the bird. A child cannot meaningfully consent to having
her legal name permanently attached to a commercial product, and a public marketing site is far
more exposed than an in-app credit. The decision belongs to her, made at an age when it is
genuinely hers to make.

**Where it is written down:** Section 6 of `legal/Artwork_Purchase_and_Copyright_Assignment.md`
in the app repo (6.2 withholds the name, 6.3 is her election, 6.4 lets her revoke it, 6.5 stops
anyone pressuring her for one). The app's About screen and this site were both scrubbed on the
same day and carry code comments saying not to re-add the name.

**Do not add her name to this site** — or to the app, the store listings, or any press or
marketing material — unless that written election exists.

## House rules for edits

- The **NMJL non-affiliation disclaimer** in the footer must stay on every page, and must match the
  wording in the app's About screen and `BUSINESS_Notes.md`. Change one, change all.
- The privacy policy describes what the code actually does today. **If the app starts collecting
  something new — analytics, accounts, crash reporting — this page changes in the same commit.**
  A privacy policy that has drifted from the code is worse than none.
