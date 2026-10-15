+++
title = "Day 02 - 13/10/2026 (Remote)"
weight = 2
+++

# Daily Report - Day 02

## 1. Today's objectives

Today I worked remotely on completing approval permissions in warehouse workflows and adding automatic cancellation for orders that have not yet been dispatched when they become overdue.

## 2. Approval permissions and assigned work

- Allowed managers with access to a warehouse to approve documents they created or documents assigned to them.
- Assigned employees can only carry out a document after it has been approved; they cannot approve it themselves.
- Added an **Approvals** tab in **Overview** to group assignments awaiting approval.
- Added an **Approvals** tab in **Outbound** to show picking documents awaiting approval separately.
- Permission and workflow tests passed.

## 3. Automatic cancellation of orders not yet dispatched

- Added a scheduled check that runs every minute for orders that have not yet been dispatched.
- Automatically changes an order to **Canceled** with the reason **“Picking deadline exceeded”** if it is still not fully picked after the deadline.
- Automatically changes an order to **Canceled** with the reason **“Delivery appointment missed”** if its scheduled delivery time has passed.

## 4. Results and summary

Completed the warehouse-scoped approval rules, clearly separating approval permissions from execution permissions, and added the appropriate **Approvals** tabs to each screen. Permission and workflow tests passed. The automatic cancellation process was also added for orders not yet dispatched, with the corresponding status and cancellation reason for overdue picking or a missed delivery appointment.
