# aigov-ops-open-source-vendor-rfi-rapp-johnston-june-2026

AiGovOps Foundation open-source Vendor RFI/RFP webapp — evidence-oriented vendor stack composer for Beacon & Umbrella, with auditor value model and neutral vendor sponsorship framework.

## Quick start

**New here? Start with the [audit-training tool](training.html)** — learn the AiGovOps governance stack, take a scored knowledge check, run a self-audit, and export a verifiable receipt.

Open `index.html` (the overview) in a browser, then "Open webapp" to launch the advisor — or open
`vendor-rfi-advisor.html` directly.

## What this is

A static site (no build step) in the AiGovOps "garden-warm" skin (`garden.css`; `tokens.css` kept for
legacy compatibility), shared with Beacon & Umbrella. Four pages plus generated docs:

- **`index.html`** — the overview / landing page: what the RFI gives auditors and vendors, the
  Beacon · Umbrella · Lantern roadmap, and links into the app and docs.
- **`vendor-rfi-advisor.html`** — the advisor webapp. Two operating views:
  - **Beacon lens** — an unsigned evidence-receipt preview (canonical JSON + SHA-256), ready for
    Beacon Ed25519 + JCS signing.
  - **Umbrella lens** — a profile-driven stack composer across audit, policy-as-code, gates/controls,
    dashboards, runtime guardrails, and shipping code, with JSON/YAML export and a light/dark toggle.
- **`comparison.html`** — side-by-side comparison of 50 (2026) AI-governance vendors across 5 categories.
- **`training.html`** — the audit-training tool (lessons, knowledge check, self-audit, completion receipt).
- **`docs/*.html`** — vendor guide, auditor value model and sponsorship model, generated from the
  Markdown in `docs/` by `scripts/md2html.py`.

The advisor's vendor data and recommendation logic are derived from `docs/vendor-guide.md`.

## Files

- `index.html` — overview / landing
- `vendor-rfi-advisor.html` — the advisor webapp (profiles → stack → recommendation → receipt)
- `comparison.html` — side-by-side comparison of 50 (2026) AI-governance vendors across 5 categories
- `training.html` — interactive audit-training tool (lessons + knowledge check + self-audit + completion receipt)
- `vendors-data.js` — the vendor dataset (single source of truth, maintained by aigovops-agent-vendor-rfi)
- `garden.css`, `tokens.css` — garden-warm design tokens and legacy brand tokens
- `docs/vendor-guide.md` — AI Governance Policy-as-Code Vendor Guide for Fortune 100 Manufacturing (source content)
- `docs/auditor-value.md` — evidence-oriented auditor value model
- `docs/vendor-sponsorship.md` — neutral sponsorship model (sponsor the surface, not the score)
- `docs/vendor-guide.html`, `docs/auditor-value.html`, `docs/vendor-sponsorship.html` — pages generated from the Markdown above
- `scripts/md2html.py` — regenerates a doc page: `python3 scripts/md2html.py docs/<name>.md "<Title>" docs/<name>.html`
- `scripts/check-site.js` — CI check: vendor-data schema + HTML link integrity (`node scripts/check-site.js`)
- `scripts/check-tokens.sh` — CI check: `tokens.css` matches the canonical foundation tokens
- `.github/workflows/ci.yml` — runs both checks on every PR and push to `main`
- `.github/workflows/freshness.yml` — quarterly catalog-freshness audit that opens a tracking issue when overdue
- `sitemap.xml`, `robots.txt`, `.nojekyll` — static hosting files
- `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `.github/ISSUE_TEMPLATE/` — contribution + governance

## Hosting

GitHub Pages serves the `main` branch from the repo root (branch deploy; `.nojekyll` turns off Jekyll
processing). There is no build step or deploy workflow: merging to `main` publishes the site at
https://aigovops-foundation.github.io/aigovops-vendor-rfi/. It can be linked or embedded from the
Beacon and Umbrella sites on www.aigovops-foundation.com.

## License

Apache-2.0.
