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
In this scenario the partner system integration will be tighter and the effort to implement it will be higher. But the synchronization of changes made in the Export Controls web application to a partner system still falls out of this scope.

![](https://files.readme.io/ab89f7e-ec2.png "ec2.png")

A user (order processor) of a partner system creates or updates a business transaction (e.g., an order). The partner system then calls, if all mandatory data was entered, a [checkTransaction()](ref:checktransaction) request with a host- system-generated transactionId using the Export Controls API.

Export Controls performs all configured checks and creates a log entry. If a restriction was detected, a *check transaction* is generated and stored in Export Controls.  A response is sent back to the partner system. The partner system uses the response [results](doc:results) to store the results along with the order. If the response suggested an export restriction, the partner system blocks the order. Additionally, the order processor may be informed about the blocked order.

Some time later, the export control officer then uses the Export Controls web application to check the created transaction and perhaps approves or rejects it. There is no automatic feedback to the partner system for this action.

Either the order processor manually triggers a re-check of the order, or a batch job can be created that runs, e.g., once a day to re-check all blocked/critical orders. Then the partner system again calls [checkTransaction()](ref:checktransaction) for the same order (using the same **transaction Id** (API: transactionIdHost)). Depending on whether the Export Control officer approved the transaction, the result of the check might now turn into "not critical". 

> 🚧 Warning
>
> Use the API [getTransactionCheckResult](ref:gettransactioncheckresult) only if the partner system can ensure, that no data in the transaction has changed in between, as this API does not trigger a new check and thus will not detect changed partners, positions, goods, etc. in the transaction.

The partner system has to evaluate the new response result, and remove the previously created blocking of the order in case the result is uncritical. Additionally, the partner system might inform the order processor about the update via a popup or other means of notification.

> 📘
>
> Use the calls of [checkTransaction()](ref:checktransaction) in moderation, as each call will be billed.

> 📘
>
> If a business transaction (e.g., an order) is deleted in the partner system, no action is required, as deletion of check transactions in the Export Controls web application is not supported and not necessary.
