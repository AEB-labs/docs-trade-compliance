---
title: Sync Events for Questionnaires
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
The [RAQuestionnaireSyncParameterDTO](https://rz3.aeb.de/test4ce/servlet/bf/doc/RiskAssessmentBF/de/aeb/xnsg/riskasmt/bf/sync/RAQuestionnaireSyncParameterDTO.html) contains the data to identify the transaction the questionnaire belongs to. The most relevant parameter to identify transactions a questionnaire belongs to is the "referenceIdHost" which is the identifier used in the partner system. If a questionnaire was created from the [Export Control BF](https://trade-compliance.docs.developers.aeb.com/docs/ec-bf-calls-overview), the parameter "referenceIdHost" is identical to the "transactionIdHost" of the Export Controls transaction.

**Which changes in a Risk Assessment questionnaire trigger a synchronization event?**
+ The deletion of the most recent questionnaire for a transaction, if the questionnaire was still valid and the transaction belongs to a subscribed host system.
+ The invalidation of the most recent questionnaire for a transaction,  if the transaction belongs to a subscribed host system.
+ The completion of the most recent questionnaire for a transaction, if the transaction belongs to a subscribed host system.

**Parameters of SyncEventDTO in response of request for new synchronization events:**
+ businessObjectType = “RAQUEST”: Code which identifies the business object type the event belongs to. In this case, this is the identifier for a Risk Assessment questionnaire.
+ businessObjectId: Unique ID of a questionnaire in Trade Compliance Management.
+ eventType: Type of the event (e.g., CREATE, UPDATE or DELETE).
+ eventDate: Date when the event happened.
+ parameter: additional parameters of a questionnaire. Generic record of <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/RiskAssessmentBF/de/aeb/xnsg/riskasmt/bf/sync/RAQuestionnaireSyncParameterDTO.html" target="_blank">RAQuestionnaireSyncParameterDTO</a> (see more information about parameters mapping in REST and SOAP documentation).