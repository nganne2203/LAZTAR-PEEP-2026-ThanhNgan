+++
title = "Day 03 - 23/09/2026 (Remote)"
weight = 3
+++

# Daily Report - Day 03

## 1. Today's learning goals

Today I focused on finalizing the Product & Supplier domain and aligning it with the project’s main business flow from the Mini-WMS Business Flow document. My goal is to clarify how product data, supplier data, UOM conversions, and stock flows connect to the warehouse processes of receiving, put-away, allocation, picking, transfer, and adjustment.

I also defined the role I will take in the project as a Frontend developer and mapped out the responsibilities and UI scope for that role.

## 2. What I did today

- Selected Domain C: Product & Supplier as the main focus of the day.
- Reviewed the Mini-WMS Business Flow document and mapped it with the main warehouse processes.
- Identified the core data entities for SKUs, UOMs, barcodes, suppliers, and SKU-supplier relationships.
- Constructed a simplified ERD to describe how Domain C interacts with inventory and stock ledger entities.
- Chose the project role as Frontend and clarified the responsibilities associated with the role.
- Confirmed the key workflow structure for the WMS project:
  - Inbound
  - Outbound
  - Transfer
  - Adjustment

## 3. Knowledge gained

### 3.1 Domain C – Product & Supplier

Domain C is the foundation of the WMS because all operational flows depend on accurate product and supplier data. If SKU data, UOM, barcode, or supplier mappings are wrong, the inventory and shipping processes will be inaccurate.

Key domain entities include:

- SKU: product master data, status, base UOM, lot tracking, and serial tracking.
- UOM: unit of measure definitions such as EA, BOX, CARTON, and KG.
- SKU-UOM Conversion: mapping between units and the base UOM.
- SKU Barcodes: barcode records for product and UOM combinations.
- Supplier: supplier master data.
- SKU Supplier: relationship between a product and a supplier, including supplier SKU code and preferred vendor flag.

The critical lesson is that all inventory quantities must be stored in base UOM for consistency during stock updates and ledger recording.

### 3.2 Business flow confirmed from the project document

The project document defines four core business flows:

1. Inbound

   - warehouse receives goods from supplier
   - system validates UOM, lot, and expiry data
   - goods are temporarily stored in receiving area
   - goods are put away into a valid storage bin
   - stock is transferred from receiving to storage location
2. Outbound

   - warehouse creates an order
   - system checks available stock and allocates inventory via FEFO logic
   - warehouse staff pick stock from the assigned bin
   - goods are packed and shipped
   - stock is reduced and the shipping history is recorded
3. Transfer

   - product is moved from one location to another within the warehouse
   - source and destination must be valid
   - total stock remains unchanged
   - location-level inventory accuracy is maintained
4. Adjustment

   - physical count is compared with system records
   - discrepancy is recorded in an adjustment request
   - approver reviews and approves or rejects the request
   - inventory and stock ledger are updated only after approval

The most important principle in the system is that stock changes must be processed through the stock ledger rather than writing directly to the inventory table.

### 3.3 Important business rules in Domain C

- Each SKU has one base UOM.
- Barcodes must be unique across the system.
- Only ACTIVE SKUs can be newly received into inventory.
- Base UOM cannot be changed after stock has already been created.
- A SKU may have multiple barcodes depending on UOM.
- One supplier can provide many SKUs, and one SKU can have many suppliers.
- Lot and expiry tracking must be applied when required by product type.

These rules connect directly to UI validation and backend business logic.

## 4. Simulated ERD for the domain and warehouse flow

This ERD illustrates the relationship between master data and operational stock data. Product data is the starting point, and inventory plus ledger data represent the real execution of warehouse tasks.

## 5. Business flow summary for the project

### 5.1 Inbound flow

- Supplier delivers goods
- system validates product, quantity, and UOM
- receiving is created and the goods remain in a receiving bay
- items are put away to the correct BIN
- inventory is updated through the stock ledger

### 5.2 Outbound flow

- order is created
- system checks stock availability and reserves it using FEFO
- warehouse picks the correct lot and location
- stock is packed and shipped
- final outbound movement is recorded in the ledger

### 5.3 Transfer flow

- items move from one location to another within the same warehouse
- source and destination are validated
- total stock stays constant
- only location allocation changes

### 5.4 Adjustment flow

- stock count is compared with actual quantity
- discrepancy triggers an adjustment request
- approver validates the request
- stock is updated only after approval

## 6. Selected role in the project: Frontend

I selected the Frontend Engineer role for the project.

### 6.1 Responsibilities

- build warehouse dashboards and overview screens
- create product and supplier master data interfaces
- design inbound and put-away forms with validation
- build order allocation, picking, and packing screens
- display stock ledger and adjustment approval pages
- ensure good UX for warehouse operators and managers

### 6.2 Why this role fits the project

This project is not just a CRUD app; it is an operational system that needs high accuracy and clear workflows. The frontend role is therefore critical because it acts as a bridge between the business process and the backend system. A strong frontend must help users avoid mistakes, show accurate stock data, and support fast decision-making in real warehouse operations.

### 6.3 Skills needed

- React + TypeScript + Next.js
- form validation and workflow management
- authentication and role-based access control
- API integration and state synchronization
- UI design for inventory, receiving, and approval flows
- error handling and operational data display

## 7. Conclusion

Day 03 clarified the project’s business foundation. Domain C continues to be the key starting point for the warehouse system because all operational flows depend on SKU, UOM, barcode, and supplier data. The business flow from the project document shows a disciplined, traceable process from receipt to shipment and adjustment, and the frontend role is essential in ensuring operators use the system correctly.

The key takeaway is that the system must combine data structure, business logic, and user experience in a single consistent design. Without accurate master data and clear warehouse workflows, the entire WMS will fail in real operations.

## 8. Next steps

- refine Domain C with a data dictionary and business rules
- connect Domain C with Inventory and Stock Ledger modules
- develop UI wireframes for receiving, put-away, and stock overview
- align naming conventions and field definitions with the rest of the team
- confirm technical implementation approach with backend and QA members
