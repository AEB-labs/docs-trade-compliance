---
title: Update existing transaction labels.
excerpt: >-
  Update the transaction label for existing export control transaction
  protocols, clearings and clearing protocols after they were created. This
  method should only be called by the SAP plugin, which always provides a
  transaction label containing "[SAP has not assigned a no. yet]" in the first
  check of a check transaction. This placeholder is supposed to be replaced with
  the help of this method (although the whole label must be passed).
api:
  file: openapi.json
  operationId: setFinalTransactionLabelHost
hidden: false
---