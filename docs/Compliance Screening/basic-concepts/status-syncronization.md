---
title: Status synchronization
deprecated: false
hidden: false
metadata:
  robots: index
---
This section is relevant to you, if you are planning to maintain your business partners' data and handle at least some matches directly in AEB Compliance Screening Web Application. When handling screening matches in our Web Application, your partner system is not automatically notified on the actions that you take (e.g. creating a Good Guy). We therefore recommend the implementation of regular **status synchronization with Compliance Screening**.

To do so, your partner system can send an additional API call to a specific [screening API function](https://trade-compliance.docs.developers.aeb.com/reference/screenaddresses-1#/) for the addresses in question, which will respond with the statuses of your business partners after you have evaluated them.

To make this synchronization as smooth as possible, we recommend you implement a field representing the compliance status of a business partner (e.g. checked/blocked/released - partner has been checked/a match has been found/match has been released) and a field for additional comments (e.g. why a business partner has been blocked).

A common use case looks like this: your partner system sends a scheduled API call to AEBs Compliance Screening (see [Bulk vs. Single Address Screening](https://trade-compliance.docs.developers.aeb.com/v4.1/update/docs/bulk-vs-single-address-screening#/)) and one of your business partners is found to possibly be on a restricted party list. You are required to evaluate that match and decide whether you are dealing with a false positive or not, for example by using AEBs Web Application. However, your decision needs to be fed back to your partner system, so false positively blocked business partners / transactions are released.

You can find a schematic representation of this [here](https://trade-compliance.docs.developers.aeb.com/v4.1/docs/screening-with-integrated-re-screen#/).
