---
title: Transactions and Items
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
In Export Controls, a **transaction** describes the export you want to check, such as a sales order or delivery. The parts of a transaction are commonly referred to as (order) **items**. For best results, transaction and item information should include as much relevant information as available. I.e., all export control numbers (classifications) for the goods of each item, as well as the business partners involved.

A transaction is uniquely identified by a **client identification code** (API: clientIdentCode) , **partner system ID** (API: clientSystemId) and **transaction ID** (API: transactionIdHost) , which has to be provided by the partner system. 

**Transaction types** (API: transactionType) are particularly important if you run checks for the US ITAR [jurisdiction](doc:jurisdictions) . You can distinguish the type of movement (company > customer, etc.) and whether identities of the goods should be created and checked.

> 📘
>
> US ITAR jurisdiction might not be configured/licensed for your client.
