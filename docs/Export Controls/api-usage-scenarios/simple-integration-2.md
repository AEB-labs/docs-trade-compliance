---
title: Simple Integration
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Let's start with a typical, simple workflow for an export control check within a transaction (e.g., a sales order), as illustrated in the diagram below. (Click the image to enlarge it.)

![1267](https://files.readme.io/6c31709-ec1_v2.png "ec1_v2.png")

A user (order processor) in the partner system creates or updates a business transaction (e.g., an order). Once all mandatory data has been entered, the partner system calls the Export Controls API's [checkTransaction()](ref:checktransaction) request with a partner-system-generated transaction ID.

Export Controls performs all configured checks and creates a log entry. If a restriction is detected, a *check transaction* is generated and stored in Export Controls. A response is then sent back to the partner system. In this scenario, the partner system does not act on the response, and no block is placed on the order.

Depending on the configuration and the check result, an export control officer is notified by email from the Export Controls software.

At a later point, the export control officer uses the Export Controls web application to review the created transaction and either approve or reject it. The partner system does not receive automatic feedback about this decision.

If the export control officer rejects the transaction, a block should be set manually in the partner system for that particular order, to prevent any further business activity related to it.

> 📘
>
> If a business transaction (e.g., an order) is deleted in the partner system, no action is required. Deleting check transactions in the Export Controls web application is neither supported nor necessary.
