---
title: Status syncronization
deprecated: false
hidden: false
metadata:
  robots: index
---
This section is relevant to you, if you are planning to maintain your business partners' data and handle matches directly in AEB Compliance Screening Web Application. In this case, we recommend the implementation of regular **status syncronization with Compliance Screening**, which **is not integrated automatically**.

To make this syncronization as smooth as possible, we recommend you implement a field representing the compliance status of a business partner (e.g. blocked/released, as in a match has been found or not) and a field for additional comments (e.g. why a business partner has been blocked).

A common use case looks like this: your partner system sends a scheduled API call to AEBs Compliance Screening (see [Bulk vs. Single Address Screening](https://trade-compliance.docs.developers.aeb.com/v4.1/update/docs/bulk-vs-single-address-screening#/)) and one of your business partners is found to possibly be on a restricted party list. You are required to evaluate that match and decide whether you are dealing with a false positive or not, using AEBs Web Application. However, your decision needs to be fed back to your partner system, so false positively blocked business partners / transactions are released. To do so, your partner system can send an additional API call to a specific screening endpoint, which will either relay the