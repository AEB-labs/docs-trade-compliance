---
title: Business Facade Calls Overview
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
Risk Assessment BF calls complement the integration of Risk Assessment in Export Controls.

The following BF calls exist:

* [getQuestionnaireSummary()](ref:getquestionnairesummary): returns a summary of the most recent valid questionnaire for the referenced Export Control transaction. This method can be used, for example, if the partner system wants to monitor the age of a questionnaire assigned to some Export Control transaction.
* [invalidateQuestionnaires()](ref:invalidatequestionnaires): invalidates (logical deletion) all questionnaires for the referenced Export Control transaction.
* [countQuestionnaires()](ref:countquestionnaires): counts the questionnaires matching the specified filter parameters. 

For example, with these additional BF calls the following use case can be realized. With the API call [getQuestionnaireSummary()](ref:getquestionnairesummary) a host system can monitor the age of a questionnaire assigned to an Export Control transaction. If the questionnaire exists and is too old, the host system can invalidate it with API call [invalidateQuestionnaires()](ref:invalidatequestionnaires), so it will be logically deleted and no longer considered by the Export Control check of the transaction. During the next Export Control check of the transaction using [checkTransaction()](ref:checktransaction), a new questionnaire will be created if needed.
