---
title: Classification
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
Different goods attributes can be used to classify a good. Depending on the [jurisdiction](doc:jurisdictions), certain goods attributes are required for an export control check. 

Some of the predefined goods attributes are:
- **ClassificationSelfDefined**: For self-defined classifications.
- **ClassificationMaterialNumbers**: For material numbers.
- **ClassificationStatisticalNumbers**: For statistical good numbers/customs commodity code.
- **ClassificationAusfuhrliste**: For EU export control numbers.
- **CLASSIFICATION_US_EAR_CCL**: For US EAR export control numbers (ECCN) (from the Commerce Control List).
- **CLASSIFICATION_US_EAR_ACTRELEVANT** with value **EAR99**:  For US EAR, to indicate that the item is classified as "EAR99" (meaning it has no ECCN but is still subject to the EAR). This goods attribute is supported only for clients using version 1 for goods attribute handling (see below).

[block:callout]
{
  "type": "info",
  "body": "Adding and editing of goods attributes can be done only in the Export Controls web application.\nThe list of **all ** defined goods attributes and their identification codes can be seen in the master data of the  Export Controls web application."
}
[/block]

[block:api-header]
{
  "title": "Indicating that an item is completely classified"
}
[/block]
Export Controls can be configured to abort the export control check of an item for a certain jurisdiction with an error if the item is not completely classified for this jurisdiction. This allows you to block the related transaction in your partner system for further processing to prevent restricted goods movements.
There are two ways to indicate whether an item has been completely classified. Which way to use depends on the version for goods attribute handling. This version is configured per client in the Export Controls web application.

[block:callout]
{
  "type": "warning",
  "body": "Your partner system must ensure that classifications are transmitted consistently with the version for goods attribute handling used by the respective client. You can view the version for goods attribute handling of a client in its settings. New customers and partner system integrations should use version 2."
}
[/block]
### Version 2 for goods attribute handling
With version 2, whether an item is completely classified is checked based only on the transmitted goods attributes. A goods attribute may only be transmitted if it was approved in the partner system during classification. This applies for all [jurisdictions](doc:jurisdictions).
To indicate that an item is not relevant for a certain jurisdiction, transmit the value “NOT_LISTED” for the corresponding goods attribute. This is possible for all goods attributes. Additionally, for US ECCNs, the value "EAR99” can be used to indicate that an item cannot be classified under a certain ECCN but is subject to the EAR. Therefore, with version 2 for goods attribute handling, transmitting the separate EAR99 goods attribute (CLASSIFICATION_US_EAR_ACTRELEVANT) results in an error.
Which goods attributes must be transmitted for a complete classification can be configured per jurisdiction in the Export Controls web application.
### Version 1 for goods attribute handling
With version 1, whether an item is completely classified is checked based on an explicit product data completion status. Your partner system has to transmit the product data completion status for the [jurisdictions](doc:jurisdictions) “EU” and “US EAR”. This is not supported for other jurisdictions.