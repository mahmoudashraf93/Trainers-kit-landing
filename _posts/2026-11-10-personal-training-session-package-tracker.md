---
layout: post
title: "Personal Training Session Package Tracker: A Free Spreadsheet Template"
description: "Track personal training session credits with a copyable spreadsheet, simple formulas and a worked example for cancellations and make-ups."
category: "THE PRACTICAL TOOLKIT"
reading_time: 6
---

When a client asks how many sessions they have left, a useful tracker should show both the balance and the events behind it. This two-sheet template works in Excel or Google Sheets. It tracks credits, not invoices or revenue, and the tables below are free to copy.

## Set the rules before tracking

Agree on how your package handles late cancellations, no-shows, expiry and make-ups before using the sheet. Put the terms in your client agreement and apply them consistently. Local rules and individual agreements may affect your terms.

For this example, a completed session uses one credit. An early cancellation uses none. A late cancellation or no-show uses one credit **only if the agreed policy says so**. A replacement for a non-chargeable cancellation does not create a new credit: the original credit was never used. If you agree to restore a forfeited credit, record a single additional credit and a note explaining why.

## 1. Create a Packages sheet

Name the first sheet `Packages`. Each row represents **one package**, even when a client buys another later. Give every package a unique ID; names alone can match multiple packages or people.

Copy this header row into cell A1:

```text
Package ID	Client	Start date	Expiry date	Purchased	Extra credits	Completed	Forfeited	Remaining
```

Enter the package ID, client, dates, purchased credits and any extra credits in columns A–F. Use `0` for extra credits when there are none. The remaining columns will calculate from the log. Restrict access and avoid including health notes in this administrative sheet.

## 2. Create a Log sheet

Name the second sheet `Log` and paste these headers into A1:

```text
Date	Package ID	Status	Note
```

Enter one row per appointment or cancellation. Use exactly these statuses:

- `Completed`: the session happened and used a credit.
- `Forfeited`: a credit was charged under the agreed policy; explain whether it was a late cancellation or a no-show in the note.
- `Cancelled - no charge`: no credit was charged; a later rescheduled session gets its own `Completed` row.

Do not count a future booking as completed. If you correct a mistake, edit the original row rather than adding a duplicate. Keep the package ID identical in both sheets.

## 3. Add the formulas

Paste these formulas into row 2 of `Packages`, then fill them down for other packages:

**G2 — completed sessions**

```text
=IF(A2="","",COUNTIFS(Log!B:B,A2,Log!C:C,"Completed"))
```

**H2 — forfeited sessions**

```text
=IF(A2="","",COUNTIFS(Log!B:B,A2,Log!C:C,"Forfeited"))
```

**I2 — remaining credits**

```text
=IF(OR(A2="",E2=""),"",E2+F2-G2-H2)
```

Columns G, H and I contain formulas; do not type into them directly. A blank package ID leaves counts blank; a blank purchased value leaves the balance blank. With a valid ID and no log entries, the counts are zero. Enter whole numbers in purchased and extra credits. If your spreadsheet locale uses semicolons as formula separators, replace the commas with semicolons.

## Worked example: one early cancellation, one late cancellation, one no-show

Ben purchases 10 sessions in package `BEN-01`. His agreement treats a late cancellation and a no-show as forfeited, but does not charge for an early cancellation. The log contains seven `Completed` rows, two `Forfeited` rows (one late cancellation, one no-show), and one `Cancelled - no charge` row. One of the seven completed sessions is the rescheduled early cancellation.

| Purchased | Extra credits | Completed | Forfeited | Remaining |
|---:|---:|---:|---:|---:|
| 10 | 0 | 7 | 2 | 1 |

The calculation is **10 + 0 − 7 − 2 = 1**. No extra credit is added for the rescheduled early cancellation, because it was never deducted. If the trainer later agrees to restore one forfeited credit, they increase Extra credits by `1`, document the decision, and the balance becomes 2. That credit is used when the replacement session is completed.

## Reconcile before renewing

At the end of each week, compare the calendar with the log: check package IDs, status, duplicate rows and any agreed credit adjustments. If a balance is negative or a client disputes it, review the underlying entries and agreement together before making a correction. Expiry dates are visible reminders; the formulas do not automatically expire credits, decide exceptions, or calculate payment.
