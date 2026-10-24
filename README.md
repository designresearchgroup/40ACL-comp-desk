# 40ACL Compliance Desk

A grant-compliance and forest-restoration tracking desk for the **40 Acre Conservation League**, built by HumanData.

It replaces the spreadsheet-and-manual-reconciliation workflow with one view of every grant, acre treated, vendor, and reporting deadline — built for the field, where there is no cell service.

## What it does (from the League's working sessions)
- **Treatment dashboard** — acres funded / treated / remaining, overall and per grant (650 funded, 400 treated, 100 remaining).
- **Grant tracker** — each grant's funder-set target acres, progress, next report, and reminder countdown (60 / 30 / 14 / 7 days).
- **Vendors & partners** — vendor reports and invoices cross-checked against internal assessments.
- **Reporting deadlines** — sorted, with time-to-due.
- **Offline field capture** — log treatment from the forest with no signal; saves on-device and marks itself *pending* until back in coverage, then syncs. Monthly email prompts to capture.

## Status — draft
- **Real** (from the interviews): the 650 / 400 / 100 acre figures, the two properties (Emigrant Gap, Leidesdorff), and the two named funders (Wildlife Conservation Board, Sierra Nevada Conservancy).
- **Sample, pending real records**: the full six-grant list, per-grant targets, vendors, deadlines. These fill in from the Phase I proposal and the League's grant files.
- Field logs persist to `localStorage` in this draft; the production build syncs to the League's secure record (Supabase).

## Run
Open `index.html` in a browser. No build step, no server.

---
HumanData · built from the 40 Acre Conservation League working sessions.
