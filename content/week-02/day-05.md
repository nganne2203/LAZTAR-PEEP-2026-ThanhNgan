+++
title = "Day 05 - 25/09/2026 (Remote)"
weight = 5
+++

# Daily Report - Day 05

- **Work mode:** Remote
- **Project:** Mini-WMS

## A. Practical work

### 1. Objective

Today I focused on the integration work and cross-review process for the project. As the owner of Domain C, which covers Product & Supplier data, I aligned my domain with the other domains and ensured that the overall ERD v1 was integrated successfully and ready for review.

The main goals were to check the connection points across domains, validate the business flow on paper, and finalize the consolidated ERD after all review feedback.

### 2. What I did today

- Participated in the 60-minute integration meeting to review the connection points defined in section 6.
- Joined the cross-review sessions with paired teams: A↔B, C↔D, D↔E, and E↔A.
- Confirmed the integration points between Domain C and the other domains, especially inventory, receiving, allocation, transfer, and adjustment flows.
- Ran business scenario tests on paper based on the project flow in section 7.
- Verified where product master data, supplier master data, UOM, and barcodes affect operational processes.
- Consolidated the ERD v1 after the review feedback and checked the merged result.
- Integrated the final ERD version into the reporting assets and confirmed that it rendered correctly.
- Documented the errors and changes processed during the review.

### 3. Domain C contribution

#### 3.1 Domain C – Product & Supplier

Domain C is the foundation of the warehouse system. Product and supplier master data determine whether the rest of the WMS processes can operate accurately. If SKU data, UOM, barcode, and supplier mapping are inconsistent, the receiving, allocation, transfer, and adjustment flows will all be unreliable.

The main entities in Domain C include:

- SKU: product master record with base UOM, status, lot control, and serial tracking.
- UOM: unit of measure definitions used in the warehouse.
- SKU-UOM Conversion: conversion rules between base UOM and operational UOM.
- Barcode: unique barcode mapping for product and UOM combinations.
- Supplier: supplier master information.
- SKU-Supplier: relationship between products and suppliers, including supplier SKU code and preferred supplier status.

The most important rule is that product and supplier data must be consistent before any stock movement can be recorded accurately.

#### 3.2 Integration points with other domains

Domain C connects directly to the core warehouse flow:

- With inventory domain: a SKU must exist before it can be stored and counted.
- With stock ledger and movement domain: every quantity change must be traced through movement records.
- With receiving flow: goods are validated by SKU, UOM, lot, and barcode before being accepted.
- With outbound flow: allocation checks availability based on SKU, lot, quantity, and UOM conversion.
- With transfer flow: storage location changes are related to SKU and inventory position.
- With adjustment flow: stock count discrepancies are created from inventory data and supplier/product metadata.

### 4. Cross-review and integration meeting

The 60-minute integration meeting was important because it helped the team spot overlapping definitions and hidden mismatches across domains.

The key points reviewed were:

- shared keys and foreign key consistency
- naming conventions across tables and APIs
- where business rules should be enforced
- how inventory and stock movements should be logged
- where Domain C impacts downstream operational modules

The cross-review sessions clarified the following pair-wise overlaps:

- A↔B: shared business flow understanding and process boundaries
- C↔D: product and supplier data mapped to inventory and movement logic
- D↔E: operational stock lifecycle connected to approval and control logic
- E↔A: final governance and control flow aligned with the core process

This helped us reduce ambiguity and align the overall design more consistently.

### 5. Business scenario validation on paper

I also ran a paper-based validation of the main business scenarios to ensure the ERD logic is consistent with actual warehouse operations.

Examples of the tested scenarios:

1. Supplier receives goods and creates a receipt record.
2. Goods are validated by SKU, UOM, barcode, lot, and expiry.
3. Inventory is updated after put-away and the stock ledger captures the movement.
4. Outbound order checks stock availability and reserves inventory.
5. Transfer updates location without changing total stock quantity.
6. Adjustment is triggered by physical count mismatch and approved by the right authority.

These scenarios validated that the design does not allow quantity changes without a proper movement record, which is critical for warehouse traceability and accountability.

### 6. ERD v1 Integration and rendering

The consolidated ERD v1 was merged after the team review and the output was successfully rendered for final validation.

![ERD tổng v1](/images/reports/day-05/ERD-V1.webp)

The integration work confirmed that the final diagram is structurally consistent and that all domains are connected through a clear flow of master data, inventory operations, and stock movement records.

### 7. Issues and changes processed

During the review, the team identified and corrected the following issues:

- duplicate or inconsistent field names across domains
- unclear relationship direction between product, inventory, and movement tables
- missing or ambiguous link between supplier and product master data
- mismatch between physical stock logic and stock ledger logic
- need to standardize base UOM and conversion handling at the domain boundary
- need to validate location and stock movement rules before final approval

The final update included corrections to the ERD model, stronger relationship definitions, and clearer operational linkage between the product domain and warehouse execution.

## B. Summary

### What I learned

- Domain C is not just a reference table layer; it drives the entire warehouse operational model.
- Integration review is necessary to detect hidden mismatches before implementation begins.
- A well-designed ERD must reflect both data structure and process logic, not only tables.
- Cross-review between pairs helps find conflicting assumptions that a single team might overlook.

### Challenges and how I handled them

- **Unclear integration boundaries:** I validated the exact connection points between Product & Supplier and the stock lifecycle.
- **Conflicting naming and relationship definitions:** I aligned the domain vocabulary and clarified cardinality.
- **Risk of incorrect stock behavior:** I reinforced the rule that all stock changes must go through movement and stock ledger records.

## C. Conclusion

Day 05 was the integration and alignment day for the project. As the owner of Domain C, I contributed not only to the product and supplier model but also to the overall design consistency across the WMS system. The cross-review meetings and paper-based scenario validation helped us identify mismatches, refine the ERD, and prepare a stronger version for implementation.

The major takeaway is that Domain C provides the foundation for the full warehouse process. When product and supplier data are correct, the receiving, inventory, transfer, adjustment, and outbound flows become stable, traceable, and easier to validate in implementation.
