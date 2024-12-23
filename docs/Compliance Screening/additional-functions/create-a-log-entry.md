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

[block:parameters]
{
  "data": {
    "0-0": "REST",
    "1-0": "SOAP",
    "0-1": "[logEntry](ref:logentry)",
    "1-1": "<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL\" target=\"_blank\">RexBF (WSDL)</a>\n<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#protocolClientSystemEvent-de.aeb.xnsg.rex.bf.ClientSystemComplianceEventDTO-\" target=\"_blank\">protocolClientSystemEvent (JavaDoc)</a>",
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
      "code": "{\n  \"level\": \"INFO\",\n  \"clientIdentCode\": \"APITEST\",\n  \"profileIdentCode\": \"DEFAULT\",\n  \"clientSystemId\": \"API-TEST\",\n  \"referenceId\": \"CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP\",\n  \"referenceComment\": \"Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP\",\n  \"info\": \"The compliance lock for order 4711 was removed.\",\n  \"userIdentification\": \"MUELLER\",\n  \"module\": \"ComplianceScreening\",\n  \"happendAtDate\": {\n    \"dateInTimezone\": \"2017-12-31 14:49:36\",\n    \"timezone\": \"GMT+01:00\"\n  }\n}",
      "language": "json"
    },
    {
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.rex.bf\">\n  <soapenv:Header/>\n  <soapenv:Body>\n    <urn:protocolClientSystemEvent>\n      <event>\n        <clientIdentCode>?</clientIdentCode>\n        <clientSystemId>?</clientSystemId>\n        <info>?</info>\n        <level>?</level>\n        <module>?</module>\n        <profileIdentCode>?</profileIdentCode>\n        <referenceComment>?</referenceComment>\n        <referenceId>?</referenceId>\n        <userIdentification>?</userIdentification>\n        <happendAtDate>\n          <dateInTimezone>?</dateInTimezone>\n          <timezone>?</timezone>\n        </happendAtDate>\n      </event>\n    </urn:protocolClientSystemEvent>\n  </soapenv:Body>\n</soapenv:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]