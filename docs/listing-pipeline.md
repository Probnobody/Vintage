# Listing pipeline: phone photo to eBay listing and Facebook draft

**Status (2026-11-15):** the one page for listing work. Written from a cloud session after Ricky lost access to the computer the work started on. It replaces the cutting rules scattered through `ebay-photo-studio.md`, `ebay-photo-studio-handoff.md`, `ebay-shoes-2026-11-12.md` and the "Photoroom only" memory on the PC. Where those disagree with this page, this page wins. Where each item stands today: [`listing-status.md`](listing-status.md). Which photos are already cut: [`../assets/cut-ledger.csv`](../assets/cut-ledger.csv).

Ricky's words, 2026-11-15: "We shouldn't be cutting pictures more than once. Claude sucks at it. We have Photoroom, Hugging Face, and Codex is good at it. We stick to what works and what we can get in to. Photos come from Apple Photos, cut, listed on eBay and draft made for Facebook Marketplace."

## The rules

1. **A photo is cut once.** Before cutting anything, look the photo up in `assets/cut-ledger.csv` (`grep IMG_2606 assets/cut-ledger.csv`, or the output name). If it has a row, it is done. Use the file in the `output` column.
2. **A re-cut needs Ricky to reject that photo.** "It could be a bit cleaner" is not a reason, and neither is a different tool becoming available. When Ricky rejects one, change its row to `status=redo`, write his reason in `note`, cut it once with a different cutter, and set the row to `final`.
3. **Three cutters, nothing else:** Photoroom, Hugging Face BiRefNet, Codex. Pick one per batch, the first on that list that can be reached from where the work is happening (table below), and write it in the ledger.
4. **Claude does not edit pixels.** No hand-made masks, no patching, no glare or colour "fixes", no straightening, no new cut-out code. Claude sorts, names, runs one of the three cutters, checks the result by eye, and records it. A bad cut means reshoot the photo or hand it to another cutter under rule 2.
5. **Close-ups are never cut.** Labels, tags, flaws, soles with size marks, tape and measurement shots go in as shot, upright and resized only. Ledger `action=keep`.
6. **Originals are never changed or deleted.** They stay in Apple Photos and in the dated Drive folder.
7. **One item, one number, everywhere.** `HWV-NN` is the eBay custom label, the Drive item folder number, the Facebook draft SKU and the row in `listing-status.md`. A new item takes the next free number before anything else happens to it.
8. **Drafts are Claude's job; going live is Ricky's.** Claude or Codex saves eBay and Facebook drafts. A listing goes live only on Ricky's word for that batch, with a price he has seen.
9. **The Facebook draft stays a draft** until Ricky says to publish it. Its price and condition must match the eBay listing. Check first whether the eBay listing already appears on Marketplace; never show the same piece twice.
10. **Nothing made up in a listing.** Size, fabric, brand and measurements come from a label photo or the tape. If it is not readable, the field stays empty and goes on the item's "to confirm" line.
11. **The session is not finished until GitHub knows.** Update the ledger and `listing-status.md`, commit and push before stopping. Drive holds photos and the sheets Ricky reads; GitHub holds the rules, the ledger, the status and the listing copy.

## The flow

| Step | What happens | Who and where | Record |
|---|---|---|---|
| 1. Shoot | Per item, in order: front, back, label, close-ups, flaws, flat on the tape. One item at a time so the photo numbers run together. | Ricky or Hollie, iPhone | Apple Photos |
| 2. Drop | Share the day's photos from Photos to a new Drive folder named for the date (`11/12` was the first). | Ricky, phone | Drive folder |
| 3. Sort | Group photos into items, give each new item its `HWV-NN`, mark each photo `cut` or `keep`, skip exact duplicates. | Claude or Codex | new rows in `listing-status.md` |
| 4. Cut | Ledger check (rule 1), then one cutter for the batch. Output 1600 px square JPEG on white. White or cream soles and silver go on light grey `EDEDED`, one background per item. | Photoroom, Hugging Face or Codex | `assets/ebay-<date>/...` plus a ledger row per photo |
| 5. Copy | Title of 80 characters or fewer, item specifics, description with the shop footer, measurements from the tape photo, packed weight and box, a price from eBay sold listings. | Claude or Codex | `assets/ebay-<date>/ready/NN-slug.txt` |
| 6. Item folder | Cut photos and the sheet go into `Holliewood eBay/Items/<NN slug>` in Drive. | `tools/ebay-drive-items.py` on a computer with Drive mounted; by hand from the phone otherwise | Drive |
| 7. eBay draft | Seller Hub draft with SKU `HWV-NN`, the HWV policies, Best Offer and Promoted Listings off. | Claude in a signed-in browser, or Ricky in the eBay app pasting from the sheet | status `draft` |
| 8. Facebook draft | Marketplace draft on Hollie's own account: same photos, same price, SKU `HWV-NN`, location set (not the Loveland default). | Claude in a signed-in browser, or Hollie in the app | status `fb draft` |
| 9. Go live | Ricky reviews the "to confirm" lines and says go. | Ricky | eBay item number in `listing-status.md` |
| 10. Push | Ledger, status, sheets committed and pushed. | whoever did the work | GitHub |

## What can be reached from where

Checked from this cloud session on 2026-11-15; the PC and Mac rows are from the dated notes in this repo.

| | Cloud session (phone or web) | A computer with signed-in Chrome | Ricky's phone |
|---|---|---|---|
| GitHub repo | yes | yes | read |
| Drive photos and sheets | yes, through the Drive connector (read, download, create files) | yes | yes |
| Hugging Face BiRefNet | yes: connector signed in, and `rembg` ran here on 2026-11-12 (29 shoe cut-outs) | yes | no |
| Photoroom | not today: the API answers 401 with no key, and the web login code never arrived on 2026-11-12 | yes, web Batch | yes, the app (Ricky ran 60 images on 2026-11-08) |
| Codex | separate Codex session on the same repo | yes | Codex app |
| eBay Seller Hub drafts | no browser session | yes | eBay app, by hand |
| Facebook Marketplace drafts | no browser session | yes | Facebook app, by hand |

So from a cloud session the work that can be finished end to end is steps 3 to 5 and 10. Steps 7 and 8 need a signed-in browser or Ricky's thumbs. To let a cloud session use Photoroom, a Photoroom API key has to be added to the cloud environment as a secret (never in the repo); `tools/photoroom-shoes/run.py` already uses it.

## Where things live

| Thing | Place |
|---|---|
| Rules, flow | this page; `CLAUDE.md` and `AGENTS.md` point here |
| Which photos are cut, by what | `assets/cut-ledger.csv` |
| Where each item stands | `docs/listing-status.md` |
| Cut photos, 1600 px | `assets/ebay-<date>/` |
| Posting sheets | `assets/ebay-<date>/ready/` |
| Shop footer, templates, customer replies | `assets/ebay-shop-kit/` |
| Facebook copy | `assets/facebook-shop-kit/` |
| eBay account state and policies | `docs/ebay-setup.md` |
| Facebook account state | `docs/facebook-marketplace.md` |
| Original photos | Apple Photos, and Drive folders named by date |
| Item folders Ricky uses on the phone | Drive `Holliewood eBay/Items/` |

## Not in GitHub

Deliberately out: keys (`.env.local`; a cloud session gets keys as environment secrets), original photos, 2048 px masters and transparent PNGs (gitignored), model weights.

Missing, and worth bringing in when a computer is reachable again:

- The photos of the 2026-11-13 batch (15 items). They were exported from the Mac's Photos library and went straight into eBay drafts. No copy was found in Drive on 2026-11-15, and none is in this repo, so they have no ledger rows.
- The "fixed" front and back photos of 2026-11-12 and Drive `Holliewood eBay/Final shots`. No note anywhere says which tool made them.
- The global rules file on the PC (`~/.claude/CLAUDE.md`: Vendor First, Plan Mode First and the rest) and the desk wiki (`dev/Chief Of Staff/wiki`). This repo refers to both and holds neither.
- Whatever the last PC and Mac sessions left uncommitted.

## Why this page exists: what went wrong

- **Six different cutters in eight days.** iPhone lift, the local model, Photoroom web, Photoroom app, BiRefNet in the cloud, and eBay's own background tool (HWV-45 on 2026-11-14). The 27 clothes fronts and backs of 2026-11-08 were cut by the local model and then again by Photoroom. The shoe set was cut with BiRefNet with a note that Photoroom "replaces them once a key exists", which would have been a second cut of 29 photos.
- **The rule changed three times and each change lived in a different file.** Local script (11/07), phone lift (11/07), Photoroom only (11/08), BiRefNet (11/12). A new session read whichever file it opened first.
- **No list of what was already cut.** Each session had to work it out from folders.
- **Work stayed on branches.** Posting sheets, the ready-to-list sheet, the shoe cut-outs and the Instagram video research each sat on their own unmerged branch.
- **The repo fell behind the shop.** `CLAUDE.md` said no clothing draft was live; Drive shows all 20 went live on 2026-11-12, and a 15-item batch was drafted on 2026-11-14 that the repo had never heard of.
- **Status went into Drive documents only**, one per session, each in its own format.
