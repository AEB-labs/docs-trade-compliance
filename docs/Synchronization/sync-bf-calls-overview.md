---
title: API Methods Overview
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
To subscribe/unsubscribe a host system to/from synchronization events the following API methods are used:

* [subscribePartnerSystem()](ref:subscribepartnersystem)
* [unsubscribePartnerSystem()](ref:unsubscribepartnersystem)
* [getPartnerSystemSubscriptions()](ref:getpartnersystemsubscriptions)

To pull the synchronization events from Trade Compliance Management there are two possible options:

* [synchronizeEvents()](ref:synchronizeevents) - The caller needs to store the last successful *SyncId* for subsequent calls
* [getNotAcknowledgedEvents()](ref:getnotacknowledgedevents) in pair with [acknowledgeEvents()](ref:acknowledgeevents) - The caller performs a handshake and acknowledges successfully processed events

More details can be found in the [REST](ref:synchronizeevents) and <a href="https://rz3.aeb.de/test4ce/servlet/bf?lang=en" target="_blank">SOAP</a> documentation.
