---
title: Integration without Synchronization
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
In this scenario, the integration with the partner system is tighter, and the implementation effort is higher. However, synchronizing changes made in the Export Controls web application back to the partner system is still outside the scope of this scenario.

![](https://files.readme.io/ab89f7e-ec2.png "ec2.png")

A user (order processor) in the partner system creates or updates a business transaction (e.g., an order). Once all mandatory data has been entered, the partner system calls the Export Controls API's [checkTransaction()](ref:checktransaction) request with a partner-system-generated transaction ID.

Export Controls performs all configured checks and creates a log entry. If a restriction is detected, a *check transaction* is generated and stored in Export Controls. A response is then sent back to the partner system, which uses the [results](doc:results) in the response to store the results alongside the order. If the response indicates an export restriction, the partner system blocks the order. Additionally, the order processor may be informed about the blocked order.

At a later point, the export control officer uses the Export Controls web application to review the created transaction and either approve or reject it. The partner system does not receive automatic feedback about this decision.

Either the order processor manually triggers a re-check of the order, or a batch job can be set up to run periodically (e.g., once a day) to re-check all blocked or critical orders. The partner system then calls [checkTransaction()](ref:checktransaction) again for the same order, using the same **transaction ID** (API: transactionIdHost). Depending on whether the export control officer approved the transaction, the check result may now be "not critical."

> 🚧 Warning
>
> Only use the [getTransactionCheckResult](ref:gettransactioncheckresult) API if the partner system can guarantee that no transaction data has changed in the meantime, as this API does not trigger a new check and therefore will not detect changes to partners, positions, goods, etc. in the transaction.

The partner system must evaluate the new response result and remove the previously created block on the order if the result is uncritical. Additionally, the partner system may inform the order processor of the update via a popup or other means of notification.

> 📘
>
> Use calls to [checkTransaction()](ref:checktransaction) in moderation, as each call is billed.

> 📘
>
> If a business transaction (e.g., an order) is deleted in the partner system, no action is required. Deleting check transactions in the Export Controls web application is neither supported nor necessary.
