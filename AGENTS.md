# Vintage (Holliewood and Vine)

Read `CLAUDE.md` in this folder for the project. This file adds the one rule Codex has been missing.

## Listing photos: cut once

`docs/listing-pipeline.md` is the process for photos, eBay listings and Facebook Marketplace drafts. Before cutting a photo, look it up in `assets/cut-ledger.csv`; if it has a row, use that output and do not cut it again. After cutting, add a row (batch, item, source, output, action, cutter, status, note). A re-cut needs Ricky to reject that photo. Labels, flaws and tape shots are never cut. Keep `docs/listing-status.md` current.

## Push when a task lands

Unpushed work is not done. When a task finishes, before a long wait, and before the session ends:

1. `git pull --rebase`
2. Grep the diff for secrets. `.env.local` is gitignored; never add it.
3. Commit only the files this task touched, with a message that says what changed.
4. `git push origin master`

If the push fails (sandbox blocks network, auth, conflict), say so in your final message with the exact error. Do not leave work uncommitted and stay quiet about it.

Pushing does not deploy. The live site is ChatGPT Sites and goes live only when it is published.
