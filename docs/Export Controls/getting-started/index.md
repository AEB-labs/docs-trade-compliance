---
title: Getting Started
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
Thank you for your interest in our Export Controls API. Please feel free to contact us if any information is missing or if you find a way to make it even easier. 

Export Controls is about checking exports against export regulations and embargos in order to comply with national and international laws.

The Export Control check covers the jurisdictions you have licensed and any manual restrictions you have defined. The result of the check is returned in the API call. Depending on how you want to make the check result visible in your system, you might want to simply ignore the result, or you might want to show the user a popup with the result info, or you might want to set a block in the transaction, until the critical status is resolved by an export control officer (ECO).  

## API

The Export Controls API allows you to check export transactions from your ERP or other host systems using [REST](ref:) or <a href="https://rz3.aeb.de/test4ce/servlet/bf?lang=en" target="_blank">SOAP</a> webservices.

> 📘 Export Controls currently has two API versions. Only the SOAP interface supports both versions. The REST interface only supports the latest version (v2). Therefore only the v2 version is documented in the following guides.

## What happens during a check via the API in the *Export Controls* product?

Detailed logs are written and, depending on notification settings, an e-mail is sent out to the export control officer with the check results and a link to the relevant log entry.\
For transactions with critical results, a persistent *check transaction* is created in the *Export Controls* web application, in which the ECO can then analyze and process the restrictions. The ECO will be supported by the system with proposals for applicable licenses.\
A restriction can be released by the ECO in the *Export Controls* web application by assigning a license. This release is represented by an *approval* data object. 

> 🚧 Processing of restrictions is not supported via API but must be performed by the export control officer in the *Export Controls* web application.

The check transactions can take into account the following criteria:

* **Export partners**:  Sellers, consignors, recipients, etc. You can add any other export partner roles that you wish to have taken into account.
* **Country** of each export partner
* **Critical End-uses**
* **Value (in one or more currencies) and quantity** of the goods 
* **Country of origin**
* **Goods attributes**: EU or DE export control number, ECCN, commodity code, material classification, etc. You can extend the goods attributes that you wish to have taken into account to include custom-defined goods attributes.