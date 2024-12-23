---
title: Sync Events for Check Transactions
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
**Which changes in an Export Controls check transaction trigger a synchronization event?**

* The deletion of a check transaction in the Export Controls web application, if the check transaction belongs to a subscribed host system.
* The deletion or creation one of the items of a check transaction in the Export Controls web application, if the check transaction belongs to a subscribed host system.
* The change of the check result from critical to uncritical (or to error) and vice versa for a transaction or one of the transaction items (e.g., after the creation of approvals) in the Export Controls web application, if the check transaction belongs to a subscribed host system.

**Parameters of SyncEventDTO in response to request for new synchronization events:**

* businessObjectType = “ECTransactionSync”: Code which identifies the business object type the event belongs to. In this case, this is the identifier for an Export Controls check transaction.
* businessObjectId:  A unique id for the transaction, the “transactionIdHost” that was provided by the host system.
* eventType: Type of the event (e.g., CREATE, UPDATE or DELETE).
* eventDate: Date when the event happened.
* parameter: Additional parameters of a check transaction. Generic record of <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/ExportControl40V2BF/de/aeb/xnsg/expctrl/bf/v40/sync/ECTransactionSyncResultDTO.html" target="_blank">ECTransactionSyncResultDTO</a> (see more information about parameters mapping in REST and SOAP documentation).

> 📘 To make the synchronization API easier to use for Export Controls check transactions, some supplementary synchronization calls were added to the Export Controls API (see also Export Controls API usage scenario [Integration with Synchronization](doc:integration-with-synchronization)).
