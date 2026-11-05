---
title: About Synchronization API
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
With the help of the synchronization API, data can be synchronized asynchronously from Trade Compliance Management to a partner system.

The synchronization API is a cross-product API and is available via [REST](ref:synchronizeevents) or <a href="https://rz3.aeb.de/test4ce/servlet/bf?lang=en" target="_blank">SOAP</a>.

## Basic concepts

In Trade Compliance Management, synchronization is available for the following business objects:

* Export Controls check transactions (businessObjectType = “ECTransactionSync”)
* Risk Assessment questionnaires (businessObjectType = “RAQUEST”)
* Compliance Screening match handling (businessObjectType = "MatchHandlingSync")

To enable synchronization for a supported business object, the partner system should subscribe to synchronization events of the corresponding type. This can be done directly in the Trade Compliance Management web application (_Office – Administration – Synchronization – Partner system subscriptions_) or via the [synchronization API](doc:sync-bf-calls-overview).

The synchronization process generally works as follows: When a partner system subscribes to synchronization events, e.g. for questionnaires, all changes to questionnaires associated with that partner system are tracked by the synchronization framework. When a significant change has been made in a questionnaire, then a journal entry is created for this event. The journal entries for synchronization events are stored in Trade Compliance Management (_Office – Synchronization – Journal entries_). A partner system can request the unprocessed synchronization events for specific business object types, analyze the returned information about the events, and take appropriate actions.

> 📘 It is specific to the different business objects which changes trigger the creation of synchronization journal entries, and this is predefined by Trade Compliance Management.