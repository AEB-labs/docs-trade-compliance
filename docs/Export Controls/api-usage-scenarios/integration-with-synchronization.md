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
In this scenario the partner system integration will be tighter and more automated therefore the effort to implement it will be higher.

To enable the synchronization for changes in Export Controls *check transactions*, a partner system should subscribe to synchronization events of Export Controls *check transactions*. This could be done directly in the Export Controls web application (*Office – Administration – Synchronization – Partner system subscriptions*) or via the [synchronization API](doc:sync-bf-calls-overview).

![1285](https://files.readme.io/c88a30b-ecWithSync.png "ecWithSync.png")

A user (order processor) of the partner system creates or updates a business transaction (e.g., an order). The partner system then calls, if all mandatory data was entered, [checkTransaction()](ref:checktransaction) with a host-system-generated transactionId using the Export Controls API.

Export Controls performs all configured checks and creates a log entry. If a restriction was detected, a *check transaction* is generated and stored in Export Controls (if it does not yet exist, otherwise the existing check transaction will be updated und rechecked). A response is sent back to the partner system. The partner system uses the response results to store the results along with the order. If the response suggested an export restriction, the partner system blocks the order. Additionally, the order processor may be informed about the blocked order.

Sometime later, an export control officer then uses the Export Controls web application to check the created transaction and perhaps approves or rejects it. If the export control officer processes the transaction in a way that affects the check results (e.g., because of approvals), a synchronization event (*journal entry*) is generated and stored in Trade Compliance Management. The synchronization events are created only if the partner system has subscribed to synchronization events for check transactions and contain information about the changed check transaction.

A batch job on the partner system should periodically call [getChangedTransactions()](ref:getchangedtransactions) to get the new results of the changed check transactions. The orders in the partner system corresponding to the changed transactions should be updated with new Export Control check results or be re-checked. The partner system must (re-)evaluate the new Export Control check result for the order and remove the previously created block in case the result is uncritical. Additionally, the partner system might inform the order processor that the order is released.

After the changed transactions are processed and the corresponding orders are updated, the partner system should call [acknowledgeGetChangedTransactions()](ref:acknowledgegetchangedtransactions) to mark the synchronization events, identified by the syncId returned in the response from [getChangedTransactions()](ref:getchangedtransactions), as processed.

> 📘 To get more information about the synchronization API and about what changes in Export Control check transactions trigger the synchronization events see [About Synchronization API](doc:about-synchronization-api).

The partner system should re-check the order if some of its data is changed or a further step in processing of the order is reached. It is also necessary to think about the reasons why an order will not be subjected to any further Export Control checks (e.g., when it is fully completed).

> 🚧 It is also important to re-check all business transactions on the partner system (except those that should be excluded) regularly, because synchronization events for Export Control check transactions do not take into account all possible changes of the environment that affect the results of Export Control check (e.g., changes in used licenses that affect their applicability).

> 📘 Use the calls of [checkTransaction()](ref:checktransaction) in moderation, as each call will be billed.

> 📘 If a business transaction (e.g., an order) is deleted in the partner system, no action is required, as deletion of check transactions in the Export Controls web application is not supported and not necessary.
