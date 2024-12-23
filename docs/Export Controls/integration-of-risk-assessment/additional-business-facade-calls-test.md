---
title: Additional Business Facade Calls
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
The Export Controls API offers an additional request [createQuestionnaireForTransaction()](ref:createquestionnairefortransaction), that explicitly creates a new questionnaire for a business transaction. It can be used, for example, if a host system wants to overrule the configuration in the compliance profile defining when a questionnaire is needed based on data in the business transaction. That means this BF call can force the creation of a new questionnaire, but only if Risk Assessment integration is active in the compliance profile.
[block:callout]
{
  "type": "info",
  "body": "See also Business Facade calls of [Risk Assessment API](doc:business-facade-calls-overview)."
}
[/block]