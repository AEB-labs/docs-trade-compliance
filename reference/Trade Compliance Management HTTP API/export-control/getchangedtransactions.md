---
title: Get the changed results of EC check transactions.
excerpt: >-
  Get the changed results of EC check transactions. Returns the changed results
  of EC check transactions, that were created for EC check transaction created
  with the *checkTransaction* call. The result of an EC check transaction might
  change if e.g. an approval was made or revoked on any of the items within
  Trade Compliance Management. Only changes relating to EC check transactions
  created by the transmitted in
  *GetChangedTransactionsRequestDTO.clientSystemId* are considered.<br>A partner
  system subscription needs to be configured in Trade Compliance Management.
api:
  file: openapi.json
  operationId: getChangedTransactions
hidden: false
---