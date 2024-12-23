---
title: Bulk vs. Single Address Screening
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
The Compliance Screening API provides two requests for address screening: [Bulk address screening](doc:bulk-address-screening) and [Find matching addresses](doc:single-address-screening). [Bulk address screening](doc:bulk-address-screening) processes several addresses at once and returns a simple result (match or not, address already defined as Good Guy). In contrast, [Find matching addresses](doc:single-address-screening) screens only one address for all matching restricted party addresses, but provides further match information.

For most use cases, you will start with [Bulk address screening](doc:bulk-address-screening) calls to find  potentially critical addresses. [Find matching addresses](doc:single-address-screening) will typically be used only in the [Match Handling](doc:restricted-party-lists) or if you plan to implement an interactive application for screening single addresses by users.
