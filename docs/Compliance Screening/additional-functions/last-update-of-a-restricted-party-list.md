---
title: Last Update of a Restricted Party List
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
Returns the date on which a restricted party list has last been updated. A date that lies some days in the past may indicate that the automated update of the data service in Trade Compliance Management is not configured properly.

This API call is typically used for technical monitoring, and may only be relevant if the AEB application is running on premise. It helps to identify situations where e.g. the automatic download of updates for restricted party lists from the data service is not working anymore because someone has blocked access to AEB in the firewall.
[block:parameters]
{
  "data": {
    "0-0": "REST",
    "1-0": "SOAP",
    "0-1": "[lastRestrictedPartyListUpdate](ref:lastrestrictedpartylistupdate-1)",
    "1-1": "<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL\" target=\"_blank\">RexBF (WSDL)</a>\n<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getLastTerrorListUpdate-java.lang.String-java.lang.String-\" target=\"_blank\">getLastTerrorListUpdate (JavaDoc)</a>",
    "h-1": "Link to documentation",
    "h-0": "Technology"
  },
  "cols": 2,
  "rows": 2
}
[/block]

[block:code]
{
  "codes": [
    {
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.rex.bf\">\n  <soapenv:Header/>\n  <soapenv:Body>\n    <urn:getLastTerrorListUpdate>\n      <client>?</client>\n      <profile>?</profile>\n    </urn:getLastTerrorListUpdate>\n  </soapenv:Body>\n</soapenv:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]