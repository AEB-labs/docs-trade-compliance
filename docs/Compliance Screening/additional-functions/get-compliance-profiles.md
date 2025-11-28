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
        [profiles](ref:profiles-1)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        SOAP
      </td>

      <td style={{ textAlign: "left" }}>
        <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL" target="_blank">RexBF (WSDL)</a>\ <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getAllProfilesForClient-java.lang.String-" target="_blank">getAllProfilesForClient (JavaDoc)</a>
      </td>
    </tr>
  </tbody>
</Table>

```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.rex.bf">
  <soapenv:Header/>
  <soapenv:Body>
    <urn:getAllProfilesForClient>
      <clientIdentCode>?</clientIdentCode>
    </urn:getAllProfilesForClient>
  </soapenv:Body>
</soapenv:Envelope>
```
