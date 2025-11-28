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

If the [Match handling and Good Guy definition](doc:restricted-party-lists) is done in Trade Compliance Management and not supported in your partner system, this API call is not relevant.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        API Variant
      </th>

      <th style={{ textAlign: "left" }}>
        Link to documentation
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        REST
      </td>

      <td style={{ textAlign: "left" }}>
        [aliasAddresses](ref:aliasaddresses-1)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        SOAP
      </td>

      <td style={{ textAlign: "left" }}>
        <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL" target="_blank">RexBF (WSDL)</a>\ <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getAliasAddresses-de.aeb.xnsg.rex.bf.AddressMatchDTO-" target="_blank">getAliasAddresses (JavaDoc)</a>
      </td>
    </tr>
  </tbody>
</Table>

```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.rex.bf">
  <soapenv:Header/>
  <soapenv:Body>
    <urn:getAliasAddresses>
      <sourceAddress>
        <aliasGroupNo>?</aliasGroupNo>
        <internalAddressId>?</internalAddressId>
        <listGroupName>?</listGroupName>
      </sourceAddress>
    </urn:getAliasAddresses>
  </soapenv:Body>
</soapenv:Envelope>
```
