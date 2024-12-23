---
title: Create a Log Entry
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
Creates a new log entry in Compliance Screening logs.

This allows you to use AEB Trade Compliance Management as a central storage for logging data to have one central application that serves as an audit trail. 

Check results of address screening are typically logged there by the AEB application. It could make sense to write additional logs about processes in the host system like blocking or unblocking of checked business partners or orders.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        Technology
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
        [logEntry](ref:logentry)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        SOAP
      </td>

      <td style={{ textAlign: "left" }}>
        <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL" target="_blank">RexBF (WSDL)</a>\ <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#protocolClientSystemEvent-de.aeb.xnsg.rex.bf.ClientSystemComplianceEventDTO-" target="_blank">protocolClientSystemEvent (JavaDoc)</a>
      </td>
    </tr>
  </tbody>
</Table>

```json
{
  "level": "INFO",
  "clientIdentCode": "APITEST",
  "profileIdentCode": "DEFAULT",
  "clientSystemId": "API-TEST",
  "referenceId": "CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP",
  "referenceComment": "Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP",
  "info": "The compliance lock for order 4711 was removed.",
  "userIdentification": "MUELLER",
  "module": "ComplianceScreening",
  "happendAtDate": {
    "dateInTimezone": "2017-12-31 14:49:36",
    "timezone": "GMT+01:00"
  }
}
```
```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.rex.bf">
  <soapenv:Header/>
  <soapenv:Body>
    <urn:protocolClientSystemEvent>
      <event>
        <clientIdentCode>?</clientIdentCode>
        <clientSystemId>?</clientSystemId>
        <info>?</info>
        <level>?</level>
        <module>?</module>
        <profileIdentCode>?</profileIdentCode>
        <referenceComment>?</referenceComment>
        <referenceId>?</referenceId>
        <userIdentification>?</userIdentification>
        <happendAtDate>
          <dateInTimezone>?</dateInTimezone>
          <timezone>?</timezone>
        </happendAtDate>
      </event>
    </urn:protocolClientSystemEvent>
  </soapenv:Body>
</soapenv:Envelope>
```
