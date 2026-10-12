+++
title = "Day 01 - 12/10/2026 (Remote)"
weight = 1
+++

# Daily Report - Day 01

## 1. Today's objectives

Today I worked remotely on the `feat(wms): improve stock ledger, location UX and outbound shelf life` feature, focusing on stock visibility, warehouse location workflows, flexible shelf-life validation, and safer outbound operations.

## 2. Stock ledger and warehouse location experience

- Added a Stock Ledger page for reviewing inventory movement history alongside accounting counterpart entries.
- Supported filtering ledger records by SKU, lot, and bin, and CSV export constrained by the selected warehouse, the user's permissions, and active filters.
- Improved the warehouse location tree to show the Zone > Rack > Bin hierarchy.
- Added a location panel showing capacity, physical stock, and inventory currently held at that location.

## 3. Shelf-life rules and warehouse data integrity

- Allowed users to set the minimum remaining shelf life per product line from 0 to 365 days; left blank, the value defaults to 2 days.
- Preserved an explicit value of 0 for products intended for urgent, same-day use, while still rejecting expired goods at receiving.
- Kept shelf-life validation consistent across the frontend, backend, and database constraints.
- Prevented warehouse deletion or deactivation while it contains stock, reserved goods, or unfinished receiving, outbound, transfer, or inventory-count documents.

## 4. Outbound, picking, and replenishment

- Added `picking_due_at` to outbound workflows and support for tracking overdue picking tasks.
- Added a product-substitution agreement flow for out-of-stock items, recording the reason, customer confirmation, agreement time, and conversion factor.
- Enabled quick stock adjustments from inventory rows or bin details while retaining permission checks, inventory-count locks, and independent-approver requirements.
- Added 50 × 30 mm product labels and package-level printing; unprinted quantities remain in staging, with delivery-batch history available for tracking.

## 5. Usability and interaction improvements

- Split receiving, product, location, outbound, return, and transfer forms into steps, with valid steps marked green, entered data retained when navigating back, and validation before saving.
- Reduced excess whitespace and organized sections around operational tasks. Tables prioritize frequently used information, stay within the available frame, scroll vertically, and provide detail views instead of requiring horizontal scrolling.
- Added distinct icons for zones, aisles, racks, and bins, and localized operational labels and approval statuses into Vietnamese.
- Preserved location and order filters in the URL and guarded against late responses showing stale data after the warehouse or user changes.

## 6. Results and summary

Completed the WMS improvements across stock ledger visibility, warehouse location management, configurable shelf-life rules, warehouse integrity protections, and outbound picking and substitution workflows. The forms, tables, labels, stock adjustment actions, and filter behavior were also refined to make common warehouse tasks clearer and safer.
