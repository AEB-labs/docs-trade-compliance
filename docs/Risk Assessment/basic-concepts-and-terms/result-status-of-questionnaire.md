---
title: Result Status of Questionnaire
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
The result status of a questionnaire can be caused by the embargo check, restricted party list screening, and/or the answers to the questions. Which result or answer leads to which result status is determined in the questionnaire template.

Result statuses can be managed in the master data in the Risk Assessment web application.

## How to obtain the result status of a questionnaire

If the questionnaire generation is integrated in the Export Controls check, the result status will be part of the response to the [ExportControl40V2BF - checkTransaction​](https://rz3.aeb.de/test4ce/servlet/bf/doc/ExportControl40V2BF/de/aeb/xnsg/expctrl/bf/v40/checktransaction/CheckTransactionRAParmsDTO.html) call as a result in the jurisdiction "RiskAssessment"

As the questionnaire might be answered asynchronously in the Risk Assessment web application, therefore to get updated results you have to synchronize the questionnaires data back to your system. For details see [Sync Events For Questionnaires](https://trade-compliance.docs.developers.aeb.com/docs/sync-events-for-questionnaires)

Alternatively the method "[RiskAssessmentBF - getQuestionnaireSummary](https://rz3.aeb.de/test4ce/servlet/bf/doc/RiskAssessmentBF/de/aeb/xnsg/riskasmt/bf/IRiskAssessmentBF.html#getQuestionnaireSummary(de.aeb.xnsg.riskasmt.bf.QuestionnaireSummaryRequestDTO))​" can be used.