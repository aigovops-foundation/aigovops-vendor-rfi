# AiGovOps Vendor RFI: notes for Claude

A static site: an overview page, a vendor-stack advisor, a comparison page and an audit-training
tool. Public repo.

## Layout

- `index.html`, `vendor-rfi-advisor.html`, `comparison.html`, `training.html`: the pages.
- `vendors-data.js`: the single source of truth for vendor data. `docs/vendor-guide.md` is what
  the data and the recommendation logic are derived from.
- `tokens.css`, `garden.css`: the shared design tokens and styles.
- GitHub Pages serves `main` from the repo root, with no build step. A merge to `main` is a publish.

## Checks to run before a pull request

```bash
node scripts/check-site.js
bash scripts/check-tokens.sh tokens.css
```

## Things that are easy to get wrong

- A vendor data change must carry a public source and a status rationale (Ready / Integrate /
  Gap), with the honest "best at" and "gap" for the entry. No source, no change.
- Neutrality is governed: ranking cannot be bought and a gap cannot be hidden. Anything touching
  sponsorship must comply with `docs/vendor-sponsorship.html`.
- `VENDOR_META.lastReviewed` records the last human audit of the catalogue. Do not bump it because
  you edited the file; `.github/workflows/freshness.yml` relies on it being true.

## Rules for an agent

- Agents propose, humans approve. Open a pull request; do not merge it, and do not push to `main`.
- Never sign, approve or rule on anything in a human's name.
- Secrets live in 1Password. Never print, paste or commit a key, token or private key.
- A check that was not run is reported as not run. Do not write "passes" from memory.
- Read `CONTRIBUTING.md` where there is one. It wins over this file where they differ.
