---
title: Sync Events for Match Handling
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
**Which changes in match handling trigger a synchronization event?**

* The creation of a good guy or processing of a match in the Compliance Screening web application, if the match belongs to a subscribed partner system.
* The change of the match handling result including undo of the previous processing for a match in the Compliance Screening web application, if the match belongs to a subscribed partner system.

**Parameters of SyncEventDTO in response to request for new synchronization events:**

* businessObjectType = “MatchHandlingSyncDigest”: Code which identifies the business object type the event belongs to. In this case, this is the identifier for a match handling sync digest.
* businessObjectId:  A unique id for the match handling sync digest, the “referenceId” that was provided by the partner system.
* eventType: Type of the event (e.g., CREATE or UPDATE).
* eventDate: Date when the event happened.
* parameter: Additional parameters of a match handling sync digest. Generic record of MatchHandlingSyncDTO (see more information about parameters mapping in REST and SOAP documentation).

> 📘 To make the synchronization API easier to use for match handling, some supplementary synchronization calls were added to the Compliance Screening API (see also Compliance Screening API usage scenario [Integration with Synchronization](doc:screening-integration-with-synchronization)).
