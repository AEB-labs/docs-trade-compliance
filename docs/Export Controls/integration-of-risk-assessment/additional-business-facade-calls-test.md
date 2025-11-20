---
title: Additional API Methods
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
The Export Controls API offers an additional request [createQuestionnaireForTransaction()](ref:createquestionnairefortransaction) that explicitly creates a new questionnaire for a business transaction. It can be used, for example, if a partner system wants to overrule the configuration in the compliance profile defining when a questionnaire is needed based on data in the business transaction. 
That means this API method can force the creation of a new questionnaire, but only if Risk Assessment integration is active in the compliance profile.

> 📘 See also API methods of the [Risk Assessment API](doc:business-facade-calls-overview).
