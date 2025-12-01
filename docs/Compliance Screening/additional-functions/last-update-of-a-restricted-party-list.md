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

This API function is typically used for technical monitoring, and may only be relevant if the AEB application is running on premise. It helps to identify situations where e.g. the automatic download of updates for restricted party lists from the data service is not working anymore because someone has blocked access to AEB in the firewall.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        API variant
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
        [lastRestrictedPartyListUpdate](ref:lastrestrictedpartylistupdate-1)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        SOAP
      </td>

      <td style={{ textAlign: "left" }}>
        <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL" target="_blank">RexBF (WSDL)</a>\ <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getLastTerrorListUpdate-java.lang.String-java.lang.String-" target="_blank">getLastTerrorListUpdate (JavaDoc)</a>
      </td>
    </tr>
  </tbody>
</Table>

```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.rex.bf">
  <soapenv:Header/>
  <soapenv:Body>
    <urn:getLastTerrorListUpdate>
      <client>?</client>
      <profile>?</profile>
    </urn:getLastTerrorListUpdate>
  </soapenv:Body>
</soapenv:Envelope>
```
