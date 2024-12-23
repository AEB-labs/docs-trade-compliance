---
title: Get Aliases of an Address
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
Returns all alias addresses of a restricted party list address.

In some restricted party lists, there are multiple names or addresses provided for the same person or company. To allow the user to see all relevant info for one found match, it is important to also present all alias entries.

If the [Match handling and Good Guy definition](doc:restricted-party-lists) is done in Trade Compliance Management and not supported in your host system, this API call is not relevant.

[block:parameters]
{
  "data": {
    "0-0": "REST",
    "0-1": "[aliasAddresses](ref:aliasaddresses-1)",
    "1-0": "SOAP",
    "1-1": "<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL\" target=\"_blank\">RexBF (WSDL)</a>\n<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getAliasAddresses-de.aeb.xnsg.rex.bf.AddressMatchDTO-\" target=\"_blank\">getAliasAddresses (JavaDoc)</a>",
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
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.rex.bf\">\n  <soapenv:Header/>\n  <soapenv:Body>\n    <urn:getAliasAddresses>\n      <sourceAddress>\n        <aliasGroupNo>?</aliasGroupNo>\n        <internalAddressId>?</internalAddressId>\n        <listGroupName>?</listGroupName>\n      </sourceAddress>\n    </urn:getAliasAddresses>\n  </soapenv:Body>\n</soapenv:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]