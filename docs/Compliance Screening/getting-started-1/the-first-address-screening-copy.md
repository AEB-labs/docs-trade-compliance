---
title: The First Address Screening (COPY)
deprecated: false
hidden: false
metadata:
  robots: noindex
next:
  pages:
    - slug: accessing-the-rest-services
      title: General parameters
      type: basic
---
To allow you to start quickly, you will find here a complete call to screen a sample address and receive a typical response. 

## Address screening

You can use this example and copy/paste it into your favorite tool to test REST and/or SOAP API calls. Our test environment is prepared to work with the data in this example.

> 📘 To reuse this example for your login details, replace the field clientIdentCode with your client, the field profileIdentCode with your Compliance profile and the field clientSystemId with an ID for your calling system.

When using REST, the URL for request in our API test environment will be [https://rz3.aeb.de/test4ce/rest/ComplianceScreening/screenAddresses](https://rz3.aeb.de/test4ce/rest/ComplianceScreening/screenAddresses).

When using SOAP, the URL for request in our API test environment will be <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL">https\://rz3.aeb.de/test4ce/servlet/bf/RexBF</a>. 

> 📘 To test REST API manually you can use this <a href="https://rz3.aeb.de/test4ce/swagger/#/" target="_blank">link</a> to our REST API documentation and click the <strong>"Try it out"</strong> button for the desired request. Do not forget to use the <strong>“Authorize”</strong> button for authentication (at the top of the web page). Otherwise, you will get a 403 HTTP error.

```json
{
  "addresses": [
    {
      "addressType": "company",
      "name": "Abu Ahmed Group Inc.",
      "street": "Fuller street 5",
      "city": "Manchester",
      "countryISO": "GB",
      "referenceId": "CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP",
      "referenceComment": "Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP"
    },
    {
      "addressType": "individual",
      "name": "John Not Existing Doe",
      "referenceId": "CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP",
      "referenceComment": "Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP"
    }
  ],
  "screeningParameters": {
    "clientIdentCode": "APITEST",
    "profileIdentCode": "DEFAULT",
    "clientSystemId": "API-TEST",
    "userIdentification": "BEN003"
  }
}
```
```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.rex.bf">
  <soapenv:Header/>
  <soapenv:Body>
    <urn:batchMatch>
      <patterns>
        <addressType>company</addressType>
        <name>Abu Ahmed Group Inc.</name>
        <street>Fuller street 5</street>
        <city>Manchester</city>
        <countryISO>GB</countryISO>
        <referenceComment>CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceComment>
        <referenceId>Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceId>
      </patterns>
      <patterns>
        <addressType>individual</addressType>
        <name>John Not Existing Doe</name>
        <referenceComment>CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceComment>
        <referenceId>Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceId>
      </patterns>
      <parms>
        <clientIdentCode>APITEST</clientIdentCode>
        <profileIdentCode>DEFAULT</profileIdentCode>
        <clientSystemId>API-TEST</clientSystemId>
        <userIdentification>BEN003</userIdentification>
      </parms>
    </urn:batchMatch>
  </soapenv:Body>
</soapenv:Envelope>
```

## Response

The referenceId in the response links the screening result with checked address from request. For more information about referenceId and referenceComment, refer to [General parameters](doc:accessing-the-rest-services) 

```json JSON
[
  {
    "matchFound": true,
    "referenceComment": "Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP",
    "referenceId": "CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP",
    "wasGoodGuy": false
  },
  {
    "matchFound": false,
    "referenceComment": "Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP",
    "referenceId": "CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP",
    "wasGoodGuy": false
  }
]
```
```xml XML (SOAP)
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
  <S:Body>
    <ns2:batchMatchResponse xmlns:ns2="urn:de.aeb.xnsg.rex.bf">
      <result>
        <matchFound>true</matchFound>
        <referenceComment>CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceComment>
        <referenceId>Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceId>
        <wasGoodGuy>false</wasGoodGuy>
      </result>
      <result>
        <matchFound>false</matchFound>
        <referenceComment>CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceComment>
        <referenceId>Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceId>
        <wasGoodGuy>false</wasGoodGuy>
      </result>
    </ns2:batchMatchResponse>
  </S:Body>
</S:Envelope>
```