---
title: Partners
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
**Partners**  (typically companies)  are related to an export process. A partner can be the seller, the consignor, the buyer, the receiver, or the final user or other partner defined in master data in the Export Controls. The following predefined partners are mandatory to use in a check transaction request:

* **CONSIGNOR\_STD**: The partner shipping an item.
* **SELLER\_STD**: The partner selling an item.
* **CONSIGNEE\_STD**: The partner receiving an item.

You can find the complete list of all defined partner roles in the master data of the Export Controls web application.

> 📘 If no buyer or final user are transmitted, then they will be automatically filled from the receiver.

> 📘 Additional partners can be added to a checkTransaction() and will be checked as well.
