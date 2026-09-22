+++
title = "Day 01 - 21/9/2026 (On-site)"
weight = 1
+++

# Daily Report - Day 01

## 1. Today's learning goals

Today I focused on understanding the project context and business model of the Mini-WMS system before implementing any feature. My goal is to understand the end-to-end warehouse workflow, project objectives, team structure, and technical constraints so that we can work effectively as a five-person team.

## 2. What I did today

- Read the project overview for FreshLink Produce and studied the business purpose of the Mini-WMS.
- Reviewed the main warehouse flow: receiving → put-away → inventory allocation → picking → packing → delivery → return.
- Analyzed the 8 key warehouse business rules that must be respected in the system.
- Studied the team formation and recommended roles: 2 Backend, 2 Frontend, 1 BA/QA, with clear responsibilities.
- Identified the technology stack: NestJS, PostgreSQL 16, Prisma, React + TypeScript + Next.js, Docker Compose, and GitHub Actions.
- Reviewed the 5-week roadmap and the deliverables expected at each stage.
- Discussed the principle of a single source of truth for stock changes and why direct table updates are not allowed.

## 3. Knowledge gained

- The project is an internal demo simulating a warehouse management system for a fictional customer, FreshLink Produce.
- The system is not just a CRUD app; it reflects real operational warehouse logic and risk.
- Key business workflow:
  - Goods receipt
  - Put-away
  - Stock allocation
  - Picking
  - Packing
  - Delivery
  - Return handling
- The most important business rules include:
  - Available inventory is not equal to physical inventory.
  - Unit conversion must be accurate.
  - FEFO is more important than FIFO for fresh goods.
  - Catch weight requires real quantity, not planned quantity.
  - Shortage handling can be managed by partial delivery, replacement, or delayed fulfillment.
  - Inventory adjustments require approval from another person.
  - Opening balance import must prevent duplicate entries.
  - Concurrency must be handled carefully to avoid negative stock.
- The project enforces a single inventory ledger service to ensure all stock changes follow one controlled process.
- Each team must follow a disciplined workflow, and the project is designed to evaluate individual ability, not only technical output.

## 4. Understanding of project architecture and execution model

From the project description, the core of the system is the InventoryLedgerService. This service is responsible for recording all stock movements and maintaining the accounting trail of inventory changes. This means that every inventory update must go through one controlled entry point instead of being edited directly in the stock table.

This helps the team avoid data inconsistency, prevents unauthorized adjustments, and makes it easier to audit history. In a warehouse system, stock is not only a number; it is a balance that must be traceable and explainable.

## 5. Challenges and concerns

- The project is business-heavy, which means we cannot focus only on code without understanding the operational logic.
- Some rules are easy to read but difficult to implement correctly, especially FEFO, catch weight, and concurrency control.
- We need to divide tasks clearly in a five-person team so that backend and frontend responsibilities are balanced.
- Since the project is evaluated by business quality and teamwork as well as code quality, we need to communicate early when blocked.

## 6. Conclusion

Week 2 Day 1 was an important orientation day. I now have a clearer understanding of the project’s purpose, business logic, and its technical/workflow constraints. More than just building features, this project is about learning how a real warehouse system works and how to work as a team under realistic business pressure.

I believe the project is suitable for a five-person team because the domain is complex, the workflow is end-to-end, and each member must understand not only coding but also business logic, review discipline, and communication.

## 7. Personal reflection

For the next steps, I need to study the 8 warehouse principles carefully and convert them into technical requirements. I also need to align with the team on responsibilities, especially around the inventory ledger service, so that we avoid duplicated logic or inconsistent implementation.

## 8. Team expectation for next steps

- Understand the project vision and clarify the business process.
- Identify the module ownership in the five-member team.
- Start the technical setup and decide the initial architecture.
- Define the backlog for the first sprint based on the Week 2–3 objectives.
- Keep communication active during standups and review sessions.
