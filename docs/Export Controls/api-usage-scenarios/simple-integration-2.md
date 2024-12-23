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
Let's start with a typical simple workflow for an export control check in a transaction (e.g., sales order) as represented in the diagram below (Click on the image to see it enlarged).

![1267](https://files.readme.io/6c31709-ec1_v2.png "ec1_v2.png")

A user (order processor) of a host system creates or updates a business transaction (e.g., an order). The host system then calls, if all mandatory data was entered, a [checkTransaction()](ref:checktransaction) request with a host-system-generated transactionId using the Export Controls API.

Export Controls performs all configured checks and creates a log entry. If a restriction was detected, a *check transaction* is generated and stored in Export Controls. A response is sent back to the host system. In this scenario the host system ignores the response and no lock is posed upon the order. 

Depending on the configuration and check result, an export control officer is notified through an email from the Export Controls software.

Some time later, the export control officer then uses the Export Controls web application to check the created transaction and perhaps approves or rejects it. There is no automatic feedback to the host system for this action.

If the export control officer rejects the transaction, a block should be set (manual process) in the host system for that particular order, to avoid further business contacts.

> 📘
>
> If a business transaction (e.g., an order) is deleted in the host system, no action is required, as deletion of check transactions in the Export Controls web application is not supported and not necessary.
