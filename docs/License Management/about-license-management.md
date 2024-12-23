---
title: About License Management
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
The lawful use of licenses is a key obligation in export controls. But managing licenses manually takes a lot of work and invites errors. License Management from AEB lets you manage all your licenses electronically – for greater efficiency and security. License Management guides you in applying for licenses, suggests the right licenses within a transaction, documents each decrement, and reports usage to the appropriate authorities. Play it safe – with export controls done right!

## API

There is no need for a dedicated REST API for License Management. All necessary functionality is provided via the Export Controls REST API.

[Please have a closer look at the usage scenarios of the Export Controls API.](doc:api-usage-scenarios)

There is a SOAP API for License Management, which should only be used in conjunction with the v1 Version of the Export Controls SOAP API, or if you want to handle the entire release process for blocked transactions, the approval selection and the revalidation process for changes to transaction data inside your own application.

While this is possible, we advise against this and refer to the approval process within the Trade Compliance Management web application that can be used with the Export Controls REST API.
