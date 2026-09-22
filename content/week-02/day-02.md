+++
title = "Day 02 - 22/09/2026 (Remote)"
weight = 2
+++

# Daily Report - Day 02

## 1. Today's learning goals

Today I focused on understanding the technical requirements and the business requirements for the Mini-WMS project. My goal is to translate the project brief into a realistic technical design and identify the main actors, user flows, and system constraints before implementation begins.

## 2. What I did today

- Reviewed the project description for FreshLink Produce and clarified the product objective.
- Studied the required technology stack: NestJS, PostgreSQL 16, Prisma, React + TypeScript + Next.js, Docker Compose, and GitHub Actions.
- Identified the key business workflow: receiving, put-away, allocation, picking, packing, delivery, and return.
- Analyzed the main functional requirements behind inventory operations and warehouse management.
- Identified the main actors in the system and their responsibilities.
- Summarized the most important non-functional requirements for reliability, traceability, and data integrity.
- Connected the business rules from the project brief to technical requirements such as single-source inventory updates and audit trail management.

## 3. Knowledge gained

### 3.1 Technical requirements of the project

From the project brief, the system is expected to be a realistic warehouse management solution for a fictional fresh-goods distributor. The selected stack and architecture are designed to support a practical operational workflow rather than a simple CRUD demo.

The required technology stack includes:

- Backend: NestJS with TypeScript
- Database: PostgreSQL 16
- ORM: Prisma
- Frontend: React + TypeScript on Next.js
- Infrastructure: Docker Compose
- CI/CD: GitHub Actions

These technologies are suitable because the system must handle:

- transactional operations,
- complex stock movement logic,
- audit trail and inventory history,
- multi-role user access,
- backend APIs for warehouse operations,
- a UI for operational staff and managers.

### 3.2 Business requirements and warehouse logic

The system is built around the real workflow of a warehouse for fresh products. The business process is not limited to storing items; it includes operational steps that affect stock accuracy and customer service.

The core flow is:

1. Goods receipt
2. Put-away into storage locations
3. Inventory allocation for orders
4. Picking
5. Packing
6. Delivery
7. Return handling when needed

The business rules show that the project focuses on operational correctness, not just interface design. The system must handle:

- available stock not equal to physical stock,
- unit conversion accuracy,
- FEFO instead of FIFO for fresh goods,
- catch weight calculations from actual measured weight,
- shortage handling with partial delivery, replacement, or delayed fulfillment,
- approval-based inventory adjustment,
- prevention of duplicate opening balance import,
- concurrency control for stock protection.

These rules translate directly into technical requirements for validation, ledger logic, transactional safety, and auditability.

## 4. Main actors in the Mini-WMS system

The project involves several key actors, each with a different purpose and responsibility in warehouse operations.

### 4.1 Warehouse Admin / System Administrator

This actor manages master data and system configuration. Typical responsibilities include:

- managing warehouse configuration,
- creating and updating product/SKU information,
- defining storage locations or bins,
- managing users and roles,
- controlling access to inventory and operational functions.

### 4.2 Warehouse Operator / Staff

This is the main operational user in daily warehouse activities. They handle:

- receiving goods,
- put-away tasks,
- stock lookup,
- picking and packing request handling,
- movement confirmation,
- reporting discrepancies to supervisors.

### 4.3 Inventory Manager / Approver

This actor is important because a warehouse system cannot allow arbitrary stock edits. Their responsibilities include:

- approving stock adjustments,
- verifying shortages and discrepancies,
- checking exceptions,
- confirming inventory adjustment before it is finalized.

This role is essential to prevent fraud and maintain operational control.

### 4.4 Supplier / Vendor

The supplier provides the items that enter the warehouse. In the system, this actor may be represented through:

- purchase order or inbound delivery information,
- product details and item quantity,
- delivery documentation and receiving records.

### 4.5 Customer / Order Holder

This actor creates demand for stock. They place orders that require the warehouse to allocate, pick, pack, and deliver items. Their order data impacts inventory reservation and fulfillment.

### 4.6 Delivery / Transportation Partner

This actor is responsible for shipping the final order from the warehouse to the customer. Their role is tied to:

- outbound delivery confirmation,
- route and shipment status,
- return pickup when necessary.

### 4.7 System / Inventory Ledger Service

Although not a human user, the inventory ledger service is a critical internal actor in the system. It acts as the single source of truth for all stock changes. This service:

- records every inventory movement,
- validates stock updates,
- prevents invalid direct modifications,
- ensures traceability and audit history.

This is the most important technical actor for the project.

## 5. Functional requirements derived from the project

Based on the brief, the system must satisfy the following functional requirements.

### 5.1 Inventory and master data management

- The system must manage warehouses, storage bins, SKUs, and product information.
- Product quantities must be stored with correct unit conversions.
- Product master data must be accurate and traceable.

### 5.2 Inbound operations

- The system must support receiving goods from supplier or purchase documents.
- Each receipt must be recorded with the correct quantity and lot or expiry information when relevant.
- The system must update stock logically through the ledger service.

### 5.3 Put-away and storage

- Items received must be assigned to a proper storage location.
- The system should support inventory tracking by location and lot.
- Storage operations must be linked to appropriate stock movement records.

### 5.4 Allocation and stock reservation

- Inventory must be allocated according to available stock, not simply total stock.
- The system must consider FEFO rules and available quantity for fresh items.
- Reserved inventory should not be treated as freely available for other orders.

### 5.5 Picking and packing

- The system must support order picking based on allocated stock.
- Picking operations must reflect actual quantities and avoid negative stock conditions.
- Packing must be linked to the order’s final dispatch state.

### 5.6 Delivery and return

- Orders must be shipped with a clear status flow.
- The system must handle shortage scenarios and return processes.
- Delivery and returns must update stock and ledger entries consistently.

### 5.7 Adjustments and approvals

- Human adjustments to inventory must require an approval process.
- The approval must be recorded to maintain accountability.
- The system must prevent unauthorized editing of the stock ledger.

## 6. Non-functional requirements

The project also has important non-functional requirements that directly affect implementation quality.

### 6.1 Data integrity

The system must guarantee that stock is correct and traceable. Invalid direct updates are not allowed because they can break the warehouse records and create reconciliation problems.

### 6.2 Transactional safety

Operations involving stock movement must be atomic. If a stock update fails halfway through, the system must avoid partial inconsistent results.

### 6.3 Auditability

Every change in inventory should leave a record. This is essential for business review, dispute resolution, and operational control.

### 6.4 Concurrency control

Because multiple users may pick and update stock at the same time, the application must handle concurrency carefully to prevent negative inventory or inconsistent stock balance.

### 6.5 Security and authorization

Different actors should have proper permissions. For example, warehouse staff should not be allowed to approve or manipulate inventory adjustments without the proper role.

### 6.6 Maintainability

The solution must be structured clearly enough to support collaboration in a five-person team and easy review of business logic.

## 7. Connection between requirements and technical design

This project demonstrates that the requirements are not only UI features; they are business rules written into a system design.

For example:

- the single-source inventory ledger is a technical response to the requirement that stock changes must be controlled,
- approval-based adjustment is a response to the need for accountability and anti-fraud protection,
- FEFO logic is a business rule that must drive stock allocation and picking,
- concurrency handling is required because warehouse transactions occur in parallel in real operations.

This means the project is a strong example of how technical implementation should follow business rules rather than only building screens.

## 8. Challenges and concerns

- The system has many business rules that are simple in concept but difficult to implement correctly.
- Some requirements require strict logic and careful data modeling, especially around stock movement and ledger history.
- There is a risk of solving the problem only from the code side without understanding the warehouse process.
- The team must coordinate roles clearly, especially regarding the single inventory ledger service and approval flow.

## 9. Conclusion

Day 02 was important because it shifted my attention from basic setup to understanding the real technical and business requirements of the Mini-WMS project. I now understand that this project is not a general CRUD system; it is a warehouse system with strict operational rules, traceability requirements, and strong controls around stock movement.

The main takeaway is that the system is driven by both technology and business logic. The architecture must support real warehouse operations, and the actors must be defined clearly so that responsibilities, permissions, and workflows are consistent.

This understanding is essential for the next stage of implementation, because every feature we build must align with the business rules and the project’s requirement model.

## 10. Personal reflection

I should continue to study the project requirements in more depth, especially the eight warehouse business rules and the role of the inventory ledger service. The more clearly I understand the domain, the easier it will be to design a correct technical solution and reduce errors during implementation.
