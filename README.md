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
- **Verified** (from the Phase I proposal): the seven funding lines — funders, purposes, and amounts ($19.83M total), the two properties (Tahoe Forest Gateway / Leidesdorff, Blue Canyon), and the portfolio figures (404.98 ac treated 2025, 700+ conserved, 20,000-acre goal).
- **Provisional, marked `[confirm]`**: each grant's reporting cadence is pre-filled from the funder's published grant guidelines — SNC = six-month progress reports + final (Managing Your Grant Handbook); WCB restoration/planning = final report + progress per agreement, annual assumed; WCB acquisition = closeout only (General Grant Guidelines §6.6). These are starting points to verify against each executed grant agreement's Exhibit A. Editing a grant and saving clears the `[confirm]` flag.
- **Not yet set**: per-grant report due dates and acre targets — left blank until read from the grant agreements (or imported via the CSV template).
- Field logs persist to `localStorage` in this draft; the production build syncs to the League's secure record (Supabase).

## Run
Open `index.html` in a browser. No build step, no server.

---
HumanData · built from the 40 Acre Conservation League working sessions.
