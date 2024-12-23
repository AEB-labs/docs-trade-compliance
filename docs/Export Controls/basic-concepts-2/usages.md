---
title: Critical End-Uses
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
The following *critical end-uses* are currently known by the standard jurisdictions in Export Controls:
- ** FINAL_USAGE_NONE **: There is no special end-use.
- ** FINAL_USAGE_ALL**: All types of end-uses are possible.
- ** DE-EU-ABC-Nuclear-Weapons**: Indicates NBC weapons incl. missile technology as end-use.
- **DE-EU-Nuclearplants**: Indicates nuclear plants as end-use.
- **DE-EU-Conventional-Weapons**: Indicates a military end-use.
- **DE-EU-IllegalExportedWeapons**: Indicates illegally exported munitions as end-use.  
- **DE-EU-Military-Consignee**: Indicates a military consignee as end-user.
- **DE-EU-Free-Trade-Zone**: Indicates that the consignee or end-user is located in a free trade zone or bonded warehouse.

Other special end-uses depend on the [jurisdictions](doc:jurisdictions) or can be configured in master data in the Export Controls and may be separated by ';' (semicolon) if more than one applies to an item.
   
[block:callout]
{
  "type": "info",
  "body": "If no end-use is set, FINAL_USAGE_NONE is automatically assumed.",
  "title": "No end-use set"
}
[/block]