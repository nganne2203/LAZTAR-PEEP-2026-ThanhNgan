+++
title = "Day 05 - 09/10/2026 (On-site)"
weight = 5
+++

# Daily Report - Day 05

## 1. Today's objectives

Today I focused on fixing the remaining UI gaps for the warehouse and stock ledger demo, updating the backend logic for receiving flow flexibility, and showing the end-to-end demo to the company for feedback.

## 2. UI improvements and demo preparation

- Added the missing Stock Ledger UI to display stock movement and balances in a clearer and more usable format.
- Improved the warehouse display so that inventory data is easier to scan at a glance, with clearer grouping, spacing, and information hierarchy.
- Refined the warehouse/stock overview to make the demo more understandable for stakeholders during the on-site presentation.
- Reviewed the flow end-to-end before the demo to ensure the receiving and stock views are consistent with the actual operational logic.

## 3. Backend logic update

- Updated the receiving logic so the user can choose the minimum shelf-life requirement for each product they receive, instead of using the fixed 2-day hardcoded rule.
- Kept the rule configurable at the product or receiving workflow level so warehouse operations can adapt to different product types and business requirements.
- Validated the logic to ensure the minimum expiry rule is applied correctly during the receiving process and reflected in downstream stock visibility.

## 4. Warehouse deletion validation

- Reviewed the issue of deleting a warehouse that still contains products.
- Confirmed that deletion should not be allowed while the warehouse still has inventory, because this would create data inconsistency and break stock traceability.
- Proposed the direction to resolve this safely: block deletion when stock remains, or require zero-stock status before deletion is permitted; if needed, move or reassign the goods first.
- This approach preserves warehouse integrity and avoids orphaned product records or invalid stock balances.

## 5. Demo to the company and feedback received

- Presented the updated warehouse and stock-related workflow to the company during the on-site demo.
- Received positive feedback on the new stock ledger visibility and the clearer warehouse display.
- The company also emphasized the importance of making the product expiry rule configurable and ensuring warehouse deletion is protected by validation rules.
- They requested that these points be polished further and validated in the next iteration to improve operational readiness.

## 6. Results and summary

The missing Stock Ledger UI was added, the warehouse display was improved for readability, the backend receiving rule was updated to allow user-selected minimum expiry days instead of a hardcoded 2-day value, and the warehouse deletion risk was validated with a safer business rule direction. The on-site demo was completed successfully and the company feedback confirmed that the current direction is aligned with operational needs, with further refinement still required before full rollout.
