---
title: Get Compliance Profiles
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
Returns all Compliance profiles of a client.
[block:parameters]
{
  "data": {
    "0-0": "REST",
    "1-0": "SOAP",
    "0-1": "[profiles](ref:profiles-1)",
    "1-1": "<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL\" target=\"_blank\">RexBF (WSDL)</a>\n<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getAllProfilesForClient-java.lang.String-\" target=\"_blank\">getAllProfilesForClient (JavaDoc)</a>",
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
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.rex.bf\">\n  <soapenv:Header/>\n  <soapenv:Body>\n    <urn:getAllProfilesForClient>\n      <clientIdentCode>?</clientIdentCode>\n    </urn:getAllProfilesForClient>\n  </soapenv:Body>\n</soapenv:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]