# Backorder Report Dashboard

## Scope — IMPORTANT

This dashboard is operated by **Murdoch Linen Plant — Branch 77**.

When updating from an "AU Weekly Back order Report" workbook:

- **Only include rows where `Branch #` = `77` (plant = "Murdoch Linen").**
- Drop every other branch (Northcote, Punchbowl, Dandenong, Darra, Murdoch Garments, etc.).
- The filter must be applied against both `AU-Stock Supported` and `AU-Made to Order` sheets.
  The NZ sheets (`NZ- Stock Supported`, `NZ- MTO`) are not relevant.

## Source label

The hero chip labelled "Source" should use a human-readable week-ending phrasing,
not the filename. Format:

```
Source: Report for W/E DD/MM/YYYY
```

Where `DD/MM/YYYY` matches the `w.e.` date on the supplied workbook.

## Files

- `index.html` — the single-page dashboard. The Branch 77 records are embedded as
  the `rawData` array inside the inline `<script>` block.
- `backorder_data.csv` — the same Branch 77 records exported to CSV for reference.
- `AU Weekly Back order Report w.e. *.xlsx` — the raw source workbook(s).

## Workbook columns (for reference)

Both `AU-Stock Supported` and `AU-Made to Order` sheets use row 2 as the header.
Key columns used by the dashboard:

| Column | Field |
|--------|-------|
| Branch # | filter on `77` |
| Date of PO | `poDate` |
| PO Ref / PO Ref# | `poRef` |
| Product Code | `productCode` |
| Product | `product` |
| Ordered Qty | `orderedQty` |
| Invoiced Qty | `invoicedQty` |
| % Delivered | `deliveredPct` |
| Backorder Qty | `backorderQty` |
| On Pick Qty | `onPickQty` |
| ETA (Mel Warehouse) | `eta` |
| Stock Type / Stock Type (Prposed) | `stockType` (`SS`, `MTO`, or `RSS`) |

`outstandingQty` is derived as `backorderQty + onPickQty`.
