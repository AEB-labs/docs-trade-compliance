---
title: Check a transaction in Export Controls.
excerpt: >-
  Check a transaction in Export Controls. This call does not imply any approval
  management in the host system. Instead, if required, for each checked
  transaction from host system a check transaction is created in Export Controls
  with the data of the transmitted transaction. This is necessary, for example,
  due to critical results in the export control check. Further export control
  checks for the corresponding transaction are done using the associated check
  transaction in Export Controls. Based on this, approvals for a transaction
  must be managed directly using the corresponding check transaction in Export
  Controls. The existing approvals for the associated check transaction are
  automatically taken into account during check of transaction from host system
  in Export Controls.
api:
  file: trade-compliance-management-http-api.json
  operationId: checkTransaction
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> 📘 Response Body
>
> Currently the response body of this request cannot be shown correctly via readme.io, so please use the response description [here](https://rz3.aeb.de/test4ce/swagger/#/Export%20Control/checkTransaction).
