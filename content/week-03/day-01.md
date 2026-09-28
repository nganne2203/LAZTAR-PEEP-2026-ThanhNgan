+++
title = "Day 01 - 28/09/2026 (On-site)"
weight = 1
+++

# Daily Report - Day 01

## 1. Today's objectives

Today I reviewed the final submission package for the project and checked all required documents before uploading them to the company Drive. The main focus was to ensure the repository, supporting documents, and audit log requirements are complete and consistent with the project standards.

## 2. Final file review before submission

Before uploading the final package to Drive, I performed a checklist to ensure each file is complete, correctly named, and aligned with the required project documentation.

### 2.1 Repository and source structure

The project is stored in a single Git repository with two main folders:

- backend/
- frontend/

This structure is important because both layers belong to the same project but are managed separately by technical responsibility. The backend handles business logic, database interaction, stock movement, and validation rules, while the frontend manages user flows, screens, and interactions.

### 2.2 Files to check before final submission

The final package should include the following items:

- Project repository link and branch information
- README file for setup and running instructions
- Backend source code folder
- Frontend source code folder
- Database design or ERD documentation
- Business flow documentation
- Sprint planning or project planning notes
- Any screen mockup or UI design documentation if available
- Technical notes and implementation records
- Final report summary for the company submission

### 2.3 Submission checklist

I checked that each file should be verified for:

- correct file name and version
- consistent naming with the project standard
- no duplicate or outdated files
- no missing supporting documentation
- no sensitive or incorrect business/customer data
- clear relation to the final project scope
- final status is ready for review by mentor and company

The goal is to avoid submitting an incomplete package or a set of files that are difficult to review.

## 3. Audit log requirement for master tables

During the final review, I also re-checked the audit log requirement for all master tables in the system. This requirement is a critical data governance rule for the project.

### 3.1 Rule for master tables

Every master table, except stock_ledger, must store the following fields:

- created_at
- created_by
- updated_at
- updated_by

These columns allow us to trace who created the record and who last updated it. This is important for data accountability, operational history, and troubleshooting.

### 3.2 Exception: stock_ledger

For the stock_ledger table, only the following fields are required:

- created_at
- created_by

This table is treated as an append-only ledger and is never edited directly. Because it records the history of stock movement, it should not be updated after creation. This preserves the integrity of inventory history and supports traceability when reviewing stock changes.

### 3.3 Why this matters

This audit log rule directly supports the business requirement that inventory changes must be transparent and traceable. It also helps prevent unauthorized changes, accidental overwrites, and inconsistent operational history.

## 4. Information for mentor/company report

For the final company report, the mentor information should be added in the reporting form before submission.

- Mentor: Anh Huy
- Purpose: include in the company report / review submission
- Email: to be confirmed with Anh Huy before final upload to the Drive

This email should be verified before the final deliverable is submitted to avoid missing or incorrect contact information in the report.

## 5. Project structure and submission scope

The project is managed in a single repository with two main folders:

- backend: server-side logic, database layer, validation, and business processing
- frontend: UI, screens, user interaction, and display logic

This repo structure is consistent with the project architecture and should be clearly described in the final submission so reviewers understand how the system is organized.

## 6. Review conclusion

Today’s review was mainly a final quality check before uploading the documents to the Drive. The key lesson is that a technical submission is not only about code; it also includes document completeness, repository clarity, business-rule accuracy, and evidence of traceability through audit fields.

I will continue to maintain the repository structure, verify the required file set, and ensure the final document package is ready for the official company submission.
