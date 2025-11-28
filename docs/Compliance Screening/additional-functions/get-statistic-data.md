---
title: Get Statistic Data
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
Returns statistic data such as number of address matches, address matches processed, address matches via file checks, or Good Guys defined. You can filter by partner system, client, client group, and time frame, but the time frame may not exceed three months.

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
        [screeningStatisticData](https://trade-compliance.docs.developers.aeb.com/reference/screeningstatisticdata)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        SOAP
      </td>

      <td style={{ textAlign: "left" }}>
        <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL" target="_blank">RexBF (WSDL)</a>\ <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#protocolClientSystemEvent-de.aeb.xnsg.rex.bf.ClientSystemComplianceEventDTO-" target="_blank">getScreeningStatisticData (JavaDoc)</a>
      </td>
    </tr>
  </tbody>
</Table>

```json
{
  "clientSystemId": "TEST_ID",
  "clientIdentCode": "APITEST",
  "userName": "API_TEST",
  "resultLanguageIsoCodes": [
    "en",
    "de"
  ],
  "clientIdentCodeToGet": "APITEST",
  "dateFrom": "2016-09-21",
  "dateTo": "2016-09-21",
  "getDataOfAllClientSystems": true
}

```
```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.rex.bf">
   <soapenv:Header/>
   <soapenv:Body>
      <urn:getScreeningStatisticData>
         <!--Optional:-->
         <request>
            <!--Optional:-->
            <clientSystemId>?</clientSystemId>
            <!--Optional:-->
            <clientIdentCode>?</clientIdentCode>
            <!--Optional:-->
            <userName>?</userName>
            <!--Zero or more repetitions:-->
            <resultLanguageIsoCodes>?</resultLanguageIsoCodes>
            <!--Optional:-->
            <clientIdentCodeToGet>?</clientIdentCodeToGet>
            <!--Optional:-->
            <dateFrom>?</dateFrom>
            <!--Optional:-->
            <dateTo>?</dateTo>
            <!--Optional:-->
            <getDataOfAllClientSystems>?</getDataOfAllClientSystems>
         </request>
      </urn:getScreeningStatisticData>
   </soapenv:Body>
</soapenv:Envelope>

```
