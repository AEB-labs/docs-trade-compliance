---
title: API Functions Overview
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
The following API functions exist:

* [checkTransaction()](ref:checktransaction): Check a transaction in Export Controls.
* [getTransactionCheckResult()](ref:gettransactioncheckresult): Gets the check result for a certain EC check transaction.
* [getChangedTransactions()](ref:getchangedtransactions): Get the changed results of EC check transactions.
* [acknowledgeGetChangedTransactions()](ref:acknowledgegetchangedtransactions): Acknowledge the changed results of EC check transactions.
* [createQuestionnaireForTransaction()](ref:createquestionnaireFortransaction): Explicitly create a new questionnaire for a transaction in Export Controls.
* [deleteTransaction()](ref:deletetransaction): Explicitly delete an existing EC check transaction.
* <Anchor label="finalizeApproval()" target="_blank" href="https://trade-compliance.docs.developers.aeb.com/reference/finalizeapproval">finalizeApproval()</Anchor>: Finalize an existing approval. 
* <Anchor label="updateCustomsData()" target="_blank" href="https://trade-compliance.docs.developers.aeb.com/reference/updatecustomsinfo">updateCustomsData()</Anchor>: Add customs data to an existing approval. Can be used, for example, to fulfill the requirements outlined in AWV (German Foreign Trade and Payments Ordinance) Section 26. 

More details can be found in the [REST](ref:checktransaction) and <a href="https://rz3.aeb.de/test4ce/servlet/bf?lang=en" target="_blank">SOAP</a> documentation.
