# lastcallinvitational.com → GitHub Pages — go-live guide

Same setup as pardstour.com, second repo. Two files ship: `index.html` (the site) and
`CNAME` (contains `www.lastcallinvitational.com`). Wix stays live until the DNS flips, so
there is zero downtime.

## 1. New repo + push (GitHub Desktop, ~5 min)
1. GitHub Desktop → File → **New repository** → name it `lastcall` → publish to
   github.com/bdcomeau (public — Pages needs public on the free plan).
2. Drop `index.html` and `CNAME` into the repo folder, commit, push.

## 2. Turn on Pages (~1 min)
github.com/bdcomeau/lastcall → **Settings → Pages** → Source: *Deploy from a branch* →
`main` / root → Save. Custom domain should auto-fill from the CNAME file; tick
**Enforce HTTPS** once it appears (can take a few minutes).

## 3. Point the domain (in Wix, ~5 min + propagation)
Your domain is managed through Wix, so this is the Wix dashboard — no registrar move.
Wix account → **Domains → lastcallinvitational.com → Advanced / Manage DNS**:

| Type | Host | Value |
|---|---|---|
| CNAME | `www` | `bdcomeau.github.io` |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

Delete/replace the existing Wix-pointing records for `www` and `@`. Propagation is usually
under an hour, sometimes up to 24. The Wix site keeps serving until it completes.

⚠ If Wix won't let you edit DNS while the domain is "connected to a Wix site", first
disconnect the domain from the site (Domains panel) — the DNS editor opens up after that.

## 4. Prove it landed
- `https://bdcomeau.github.io/lastcall/` works immediately after step 2 — that's the
  pre-DNS preview.
- After DNS: `https://www.lastcallinvitational.com` serves the new site, padlock present.

## 5. Updating the site later
Same as pardstour: edit `index.html`, push from GitHub Desktop, live in ~a minute. One
file, no build step.

## Content status — REAL, pulled from the live Wix site (Aug 12 2026)
Filled in: all 39 Armand Comeau Cup champion teams 1987–2025 with results-PDF links,
both award stories (Armand + Bill Keeley), all Keeley recipients, contact
(Ryan Lauber · ryan@ryanlauber.com · 780-717-4861), and the SmugMug archive button
(brucecomeau.ca → Last Call Invitational).

## ⚠ Before retiring the Wix site — two dependencies still live there
1. **Results PDFs (1997–2025).** The champions table links to
   `lastcallinvitational.com/_files/ugd/...` — those die with Wix. Download each PDF
   (they're linked on the current Past Champions page), drop them in a `results/` folder
   in the repo as `results/2025.pdf` etc., and I'll re-point the table links in one pass.
2. **Photos.** Hero, gallery tiles, and the two award portraits hotlink
   `static.wixstatic.com`. Replace with SmugMug image URLs or files in the repo — every
   spot is marked `SWAP` in index.html. As the photographer you can grab direct image
   URLs from your own galleries; send them over and I'll wire them in.

## Optional: in-page slideshow
The Gallery page links out to the archive. For an embedded slideshow: SmugMug →
open the gallery → **Share → Embed** → copy the iframe → paste it at the marked comment
in the Gallery section (SmugMug blocks robots, so I can't generate that embed code
for you — it's a 30-second copy-paste on your side).

md5 of the index.html in this kit: `4cb8bb47e84738277bfa72e6a24af449` (38,296 B).
