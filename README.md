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
- Grants and field logs sync to the League's shared record (Supabase); `localStorage` is the offline cache, so the desk keeps working in the field and reconciles when back online.

## Run
Open `index.html` in a browser. No build step, no server.

- **Local only:** open it as-is — everything saves on-device (the status pill reads *local only*).
- **Synced across devices:** open it once with the desk key — `…/index.html?k=<desk key>` — and it connects to the shared record, pulls the live portfolio, and writes every change back. The key is stored on the device and the URL is cleaned; the pill reads *synced*. (The desk key is a shared secret — it is **not** in this repo; get it from HumanData.)

## Backend (Supabase)
All server state lives in the `fortyacl` schema of the HumanData Supabase project, reached only through token-gated `SECURITY DEFINER` RPCs — the published page carries the public anon key, and every call must present the desk key, so the data is never exposed directly.
- **Persistence:** `fortyacl_state` (load), `fortyacl_sync` (save the whole desk), plus per-entity `fortyacl_save_grant` / `fortyacl_delete_grant` / `fortyacl_save_log`.
- **Email reminders:** a daily `pg_cron` job (`fortyacl-report-reminders`) sends a due-report digest via Resend. **Gated off** (`config.reminders_live = false`) until the recipient is confirmed — set `reminder_email` and flip `reminders_live` to `true` to go live.
- **Auto-drafted reports:** `fortyacl_draft_report(grant)` assembles a reviewer-ready progress report (award, cadence, reporting period, treated-acre summary, field-log table, source basis) from the shared record — the "Draft report" button on each grant.

---
HumanData · built from the 40 Acre Conservation League working sessions.
