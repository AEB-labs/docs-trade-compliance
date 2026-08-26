---
title: Integration with Synchronization
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
In this scenario, the integration with the partner system is tighter and more automated, and therefore the implementation effort is higher.

To enable synchronization of changes to Export Controls *check transactions*, a partner system should subscribe to synchronization events for Export Controls *check transactions*. This can be done directly in the Export Controls web application (*Office – Administration – Synchronization – Partner system subscriptions*) or via the [synchronization API](doc:sync-bf-calls-overview).

![1285](https://files.readme.io/c88a30b-ecWithSync.png "ecWithSync.png")

A user (order processor) in the partner system creates or updates a business transaction (e.g., an order). Once all mandatory data has been entered, the partner system calls the Export Controls API's [checkTransaction()](ref:checktransaction) request with a partner-system-generated transaction ID.

Export Controls performs all configured checks and creates a log entry. If a restriction is detected, a *check transaction* is generated and stored in Export Controls (or, if one already exists, it is updated and re-checked). A response is then sent back to the partner system, which uses the response results to store the results alongside the order. If the response indicates an export restriction, the partner system blocks the order. Additionally, the order processor may be informed about the blocked order.

At a later point, an export control officer uses the Export Controls web application to review the created transaction and either approve or reject it. If the export control officer processes the transaction in a way that affects the check results (e.g., through an approval), a synchronization event (*journal entry*) is generated and stored in Trade Compliance Management. Synchronization events are created only if the partner system has subscribed to synchronization events for check transactions, and they contain information about the changed check transaction.

A batch job on the partner system should periodically call [getChangedTransactions()](ref:getchangedtransactions) to retrieve the updated results of the changed check transactions. The corresponding orders in the partner system should then be updated with the new Export Controls check results, or re-checked. The partner system must (re-)evaluate the new Export Controls check result for the order and remove any previously created block if the result is now uncritical. Additionally, the partner system may inform the order processor that the order has been released.

Once the changed transactions have been processed and the corresponding orders updated, the partner system should call [acknowledgeGetChangedTransactions()](ref:acknowledgegetchangedtransactions) to mark the synchronization events identified by the syncId returned in the response from [getChangedTransactions()](ref:getchangedtransactions) as processed.

> 📘 For more information about the synchronization API and about which changes to Export Controls check transactions trigger synchronization events, see [About Synchronization API](doc:about-synchronization-api).

The partner system should re-check the order whenever its data changes or when it reaches a further step in processing. It is also worth considering the circumstances under which an order should no longer be subject to Export Controls checks (e.g., once it is fully completed).

> 🚧 It is also important to regularly re-check all business transactions in the partner system (except those that should be excluded), because synchronization events for Export Controls check transactions do not account for every possible change in the environment that could affect the check result (e.g., changes to licenses that affect their applicability).

> 📘 Use calls to [checkTransaction()](ref:checktransaction) in moderation, as each call is billed.

> 📘 If a business transaction (e.g., an order) is deleted in the partner system, no action is required. Deleting check transactions in the Export Controls web application is neither supported nor necessary.
