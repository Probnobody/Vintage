# Handoff for Claude: list the 11 garments HWV-66 to HWV-76 on eBay

**Written 2026-11-17 from a cloud session that could not reach eBay.** Run this from a computer with Chrome signed in to eBay seller `holliewoodandvinellc` (Claude in Chrome: pick Browser 1 with `select_browser`; screenshots time out, read the DOM). Do not ask Ricky to sign in again.

**Ricky's instruction (2026-11-17):** "write claude a handoff to list these. make sure to list them all. make sure you update me on anything not listed." Earlier, 2026-11-16: "list and leave possible flaws."

So the goal is **all 11 live**, not drafts, with the flaw wording kept. Anything that cannot go live gets reported to Ricky with the reason.

## What you are listing

One listing per garment. Everything is in Drive, `Holliewood eBay/eBay-2026-11-15` (folder id `1DhKq2rSKJbQq0IM3FWVWcHAnEpAE2Vjf`), one folder per garment:

- `listing.txt`: the posting sheet (template, category, SKU, policies, title, description, item specifics). The same sheets are in this repo at `assets/ebay-2026-11-15/ready/`.
- `eBay-upload/`: the listing JPEGs. Upload in filename order; `01-...` is Main. Use them as supplied. Do not edit, crop or re-cut any photo.
- `transparent-cutouts/`: PNGs, not for eBay.

| SKU | Folder | Photos |
|---|---|---|
| HWV-66 | `01-Gusto-brown-knit-L` | 5 |
| HWV-67 | `02-FP-Movement-blue-hooded-top-XS` | 6 |
| HWV-68 | `03-ZESICA-orange-pink-checkerboard-M` | 6 |
| HWV-69 | `04-Earthbound-Trading-bell-sleeve-S` | 5 |
| HWV-70 | `05-Body-Central-metallic-gold-jacket-XL` | 6 |
| HWV-71 | `06-Verty-red-print-tank-L` | 5 |
| HWV-72 | `07-Zara-cream-open-knit-M` | 5 |
| HWV-73 | `08-Nike-Trail-Repel-olive-vest-M` | 8 |
| HWV-74 | `09-Diane-Gilman-silk-print-jacket-M` | 6 |
| HWV-75 | `10-Zara-sheer-abstract-stripe-tie-front-S` | 6 |
| HWV-76 | `11-Croquet-Club-teal-silk-fringe-M` | 7 |

## Before the first listing

1. In Seller Hub, search active listings and drafts for each brand. Records show no duplicate, but the live account was never checked. If one of the 11 is already live or drafted, do not make a second listing: note it for Ricky.
2. Confirm custom labels `HWV-66` to `HWV-76` are unused. If any is taken, use the next free numbers, keep the same order, and tell Ricky the new mapping.

## For each garment

1. Start from the template `HWV | Clothing | 2 day | 30 day` and **change the category** (the template is stuck on Antiques). The sheet gives a search phrase; eBay's picker decides the path.
2. Paste the title and description exactly as written in `listing.txt`. **Keep the condition line with its "Noted from the photos" flaws.** Do not soften, remove or add flaws.
3. Upload the photos in filename order and check the count against the table above.
4. Custom label `HWV-NN`. Buy It Now, quantity 1. Policies as on the sheet (HWV Parcel calculated, HWV Returns 30 days, HWV Payment immediate). Best Offer off, Promoted Listings off.
5. Condition field: **Pre-owned**. Use New with tags only for the FP Movement top (67) or Nike vest (73), and only if the full-view photos show the tags attached to the garment; photographed loose tags do not count.
6. Fill the open fields by the rules below, then publish.
7. After publishing, open the buyer page and check: title, Main photo is `01`, photo count, price, returns and handling. Record the eBay item number.

## The open fields, and how to settle each

- **Price.** Every sheet is blank. Search eBay sold listings (Sold + Completed) for the brand and garment type, and price near the 75th percentile of comparable sold items, the same way the 2026-11-12 batch was priced. Keep the comps you used. If there are fewer than about five comps, price from the nearest comparable brand and mark it "thin comps" in the report.
- **Packed weight and box.** No scale reading exists. Estimate the way `docs/ebay-weights-2026-11-12.md` did (light top about 8 to 12 oz in a 12x10x2 mailer; sweater or jacket about 1 lb to 1 lb 8 oz in 14x11x3) and mark every one as an estimate in the report.
- **[Bracketed] item specifics.** Open the tag photo in the `eBay-upload` folder and read it by eye. Enter only what the tag shows. If it is not readable, leave an optional field empty. Never guess a fabric (rule 10 in `docs/listing-pipeline.md`).
  - HWV-70 gold jacket: the fabric lines (polyurethane with rayon backing; polyester) were not confirmed. Read `06-brand-size-fiber-tag-IMG_7312.jpg`.
  - HWV-66: confirm which fibre is 55% and which is 45% on `05-brand-size-fiber-tag-IMG_7286.jpg`.
  - HWV-67, 72, 75: confirm the brand word on the sewn label matches the title.
- **Department** (HWV-73 Nike vest, HWV-76 Croquet Club shirt). Decide from the label, the cut and button side in the photos, or the style code on the Nike hangtags. If it cannot be settled, use Unisex Adults where eBay offers it. If eBay requires Men or Women and nothing in the photos decides it, do not list that piece: report it.
- **HWV-75 Zara sheer top.** The `Pit to pit: ____ in` line has no safe number. Delete that one line from the description and list it with the length only. Tell Ricky the chest measurement is missing.
- **Measurements.** Use only the numbers on the sheet. The ones marked (?) in `docs/ebay-measurements-2026-11-15.md` were left out on purpose; do not add them.

## What stops a piece from going live

Only these: it is already listed or drafted; eBay requires a field that cannot be read from the photos (Department, Size, Brand); a photo will not upload; eBay rejects the listing. Do not hold a piece back for an estimated weight, thin comps or an empty optional specific. If a piece is blocked, save it as a draft with everything else filled in and move on to the next one.

## Do not touch

Other live listings, messages, offers, payouts, Store subscription, business policies, the Facebook draft. No photo edits. No Facebook Marketplace work in this task.

## When you finish

1. Update `docs/listing-status.md`: move the 11 into a "live since" table with price and eBay item number; note any left as draft and why. Add the final SKU mapping if numbers changed.
2. `git pull --rebase`, secrets grep, commit, push.
3. Report to Ricky, one row per garment, **all 11 rows even if nothing went wrong**:

| SKU | Item | Live or not | eBay item number | Price and how many comps | Weight used (estimate) | Anything changed from the sheet | Needs Ricky |
|---|---|---|---|---|---|---|---|

Then a short list headed **Not listed**, naming each piece that is not live and the exact reason, or the words "All 11 are live." Put that list first if anything is not listed.

Things Ricky should hear about even when the piece is live: prices set from thin comps; every weight is an estimate until weighed; HWV-75 has no chest measurement; HWV-70 runs small and says so; most backs were never inspected for flaws; any specific left empty.
