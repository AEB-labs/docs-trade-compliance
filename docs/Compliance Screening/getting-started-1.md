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
Thank you for your interest in our Compliance Screening API. We would like to make it as easy as possible for you to start using Compliance Screening. Please feel free to contact us if any information is missing or if you find a way to make it even easier.

Compliance Screening is about checking addresses against [restricted party lists](doc:compliance-profile) to comply with national and international law. Examples of addresses to check are:
+ Prospective customers
+ Business partners (buyer and consignee of a sales order, supplier of goods)
+ Employees

To avoid any misunderstandings, it’s important to clarify that the transaction referred to as an “address” or an “address screening” in the documentation is primarily a name check. This name check also takes the address into account to narrow down the screening results. It is not possible to screen data based on an address alone without a name.

The Compliance Screening API allows you to screen addresses from your ERP or other host systems using [REST](ref:) or <a href="https://rz3.aeb.de/test4ce/servlet/bf?lang=en" target="_blank">SOAP</a> webservices.

Let's start with a typical workflow for screening address(es) in a transaction (e.g., sales order) as represented on the diagram below. Of course, other workflows for address screening are also possible.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/9166574-7aa026f-AddressScreeningDiagram1.png",
        "7aa026f-AddressScreeningDiagram[1].png",
        960,
        680,
        "#f6f6f6"
      ],
      "caption": ""
    }
  ]
}
[/block]