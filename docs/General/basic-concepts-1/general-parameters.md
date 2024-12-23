---
title: General Parameters
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
##Client
Basic parameters for most of the requests in Trade Compliance Management APIs are a client identification code and user. A client clusters different users into a group that share the same data, organizational unit, and so on. Typically your company gets assigned one such client, when contracting with AEB.
[block:callout]
{
  "type": "info",
  "body": "Usually client and user must be passed twice, once for authentication as described in [Setting up your environment](doc:setting-up-your-environment-1), and once as part of the general data of a request. This is because, in some contexts, the user used for authentication does not have to be the same as the user that should be used for i.e. logging in."
}
[/block]
##Compliance profile
Most of the requests require a profileIdentCode, identifying a Compliance profile. A Compliance profile is a set of settings, such as the restricted party lists to use for address screening or activated jurisdictions for export controls. Every client can have multiple profiles for different scenarios. The profile "DEFAULT" is typically available to most clients, especially in the API test environment.