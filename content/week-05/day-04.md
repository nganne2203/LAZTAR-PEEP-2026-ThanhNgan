+++
title = "Day 04 - 15/10/2026 (On-site)"
weight = 4
+++

# Daily Report - Day 04

## 1. Today's objectives

Today I focused on completing a series of improvements regarding access control, outbound assignment and execution workflows, UI and shared component synchronization, date validation rules, capacity alerts, stock-taking location exclusion, and list API sorting optimization.

## 2. Access control and post-assignment workflow

- Synchronized UI with user permissions: Disabled action buttons when users lack operational permissions; hid tabs and menus and blocked direct URL access when users lack view permissions.
- Locked unauthorized outbound steps: Dimmed steps outside the user's authority and displayed notifications to hand off work to the next assigned actor.
- Managed assignment and re-assignment: Locked the selection field once assigned; introduced a "Change ticket" button, requiring re-approval whenever the assignee changes.
- Strictly controlled post-assignment execution rights: Enforced that only the designated assignee, with sufficient permissions and an approved status, can perform actions; filtered eligible staff by stage and assigned warehouse.
- Filtered work lists by assignment: Staff members view only tasks assigned to them; managers view tasks within their warehouse scope. Separated task assignments across picking/packing and handover stages.

## 3. UI synchronization and shared component standardization

- Standardized detail view actions: Unified the view action using an eye icon, eliminated duplicate buttons and columns, opened full detail screens directly, and displayed the assignee's full name.
- Synchronized the Transfer page: Reused shared components across both tabs, placed them consistently beneath the description, and standardized the size and icon of the "Create ticket" button.
- Unified the item selection form component: Reused the shared item-picker component across inbound, outbound, putaway, transfer, substitution, supplier, price list, barcode, and reporting screens.
- Standardized status badges and metric cards: Translated all statuses to Vietnamese with semantic color-coding; preserved card colors even when metrics equal 0; verified responsive layouts on both desktop and mobile.

## 4. Warehouse business logic and data validation

- Manufactured date (MFG) and expiration date (EXP) validation: Applied rules where MFG ≥ today and EXP ≥ MFG, allowing matching dates; retained QC warnings.
- Streamlined capacity overflow alerts: Displayed alert banners only when location overflow occurs, with popup modal support for inspection and location handling.
- Refined error notifications and scale weight results: Simplified validation to display concise inline messages, removed redundant duplicate lock alerts, displayed the latest weight prominently, and collapsed weight history.
- Converted carrier input to a dropdown: Made selecting a carrier mandatory prior to goods dispatch.
- Excluded locations under stock-taking from selection: Prevented choosing locations undergoing stock counts in inbound, outbound, putaway, transfer, transit, and return/QC flows; added re-validation to block execution on pre-opened documents.

## 5. Query optimization and list sorting

- Updated default sorting for list retrieval (GET ALL) APIs: Ordered by creation date descending, falling back to ID descending for identical timestamps.
- Verified and ensured consistent behavior across all 19 list APIs.

## 6. Results and summary

Completed all 15 tasks covering access control, UI standardization, and warehouse workflow integrity: enforcing post-assignment execution rights, filtering task lists, standardizing detail views, item pickers, transfer pages, and badges, as well as applying MFG/EXP validations, stock-taking location exclusions, scale weighing refinements, and sorting for all 19 GET ALL APIs.
