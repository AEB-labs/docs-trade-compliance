---
title: The First Address Screening
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
  pages:
    - type: basic
      slug: accessing-the-rest-services
      title: General parameters
---
To allow you to start quickly, you will find here a complete call to screen a sample address and receive a typical response. 

##Address screening
You can use this example and copy/paste it into your favorite tool to test REST and/or SOAP API calls. Our test environment is prepared to work with the data in this example.
[block:callout]
{
  "type": "info",
  "body": "To reuse this example for your login details, replace the field clientIdentCode with your client, the field profileIdentCode with your Compliance profile and the field clientSystemId with an ID for your calling system."
}
[/block]
When using REST, the URL for request in our API test environment will be https://rz3.aeb.de/test4ce/rest/ComplianceScreening/screenAddresses.

When using SOAP, the URL for request in our API test environment will be <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL">https://rz3.aeb.de/test4ce/servlet/bf/RexBF</a>. 
[block:callout]
{
  "type": "info",
  "body": "To test REST API manually you can use this <a href=\"https://rz3.aeb.de/test4ce/swagger/#/\" target=\"_blank\">link</a> to our REST API documentation and click the <strong>\"Try it out\"</strong> button for the desired request. Do not forget to use the <strong>“Authorize”</strong> button for authentication (at the top of the web page). Otherwise, you will get a 403 HTTP error."
}
[/block]

[block:code]
{
  "codes": [
    {
      "code": "{\n  \"addresses\": [\n    {\n      \"addressType\": \"company\",\n      \"name\": \"Abu Ahmed Group Inc.\",\n      \"street\": \"Fuller street 5\",\n      \"city\": \"Manchester\",\n      \"countryISO\": \"GB\",\n      \"referenceId\": \"CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP\",\n      \"referenceComment\": \"Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP\"\n    },\n    {\n      \"addressType\": \"individual\",\n      \"name\": \"John Not Existing Doe\",\n      \"referenceId\": \"CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP\",\n      \"referenceComment\": \"Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP\"\n    }\n  ],\n  \"screeningParameters\": {\n    \"clientIdentCode\": \"APITEST\",\n    \"profileIdentCode\": \"DEFAULT\",\n    \"clientSystemId\": \"API-TEST\",\n    \"userIdentification\": \"BEN003\"\n  }\n}\n",
      "language": "json"
    },
    {
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.rex.bf\">\n  <soapenv:Header/>\n  <soapenv:Body>\n    <urn:batchMatch>\n      <patterns>\n        <addressType>company</addressType>\n        <name>Abu Ahmed Group Inc.</name>\n        <street>Fuller street 5</street>\n        <city>Manchester</city>\n        <countryISO>GB</countryISO>\n        <referenceComment>CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceComment>\n        <referenceId>Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceId>\n      </patterns>\n      <patterns>\n        <addressType>individual</addressType>\n        <name>John Not Existing Doe</name>\n        <referenceComment>CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceComment>\n        <referenceId>Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceId>\n      </patterns>\n      <parms>\n        <clientIdentCode>APITEST</clientIdentCode>\n        <profileIdentCode>DEFAULT</profileIdentCode>\n        <clientSystemId>API-TEST</clientSystemId>\n        <userIdentification>BEN003</userIdentification>\n      </parms>\n    </urn:batchMatch>\n  </soapenv:Body>\n</soapenv:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]
##Response
The referenceId in the response links the screening result with checked address from request. For more information about referenceId and referenceComment, refer to [General parameters](doc:accessing-the-rest-services) 
[block:code]
{
  "codes": [
    {
      "code": "[\n  {\n    \"matchFound\": true,\n    \"referenceComment\": \"Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP\",\n    \"referenceId\": \"CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP\",\n    \"wasGoodGuy\": false\n  },\n  {\n    \"matchFound\": false,\n    \"referenceComment\": \"Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP\",\n    \"referenceId\": \"CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP\",\n    \"wasGoodGuy\": false\n  }\n]",
      "language": "json",
      "name": "JSON"
    },
    {
      "code": "<S:Envelope xmlns:S=\"http://schemas.xmlsoap.org/soap/envelope/\">\n  <S:Body>\n    <ns2:batchMatchResponse xmlns:ns2=\"urn:de.aeb.xnsg.rex.bf\">\n      <result>\n        <matchFound>true</matchFound>\n        <referenceComment>CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceComment>\n        <referenceId>Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceId>\n        <wasGoodGuy>false</wasGoodGuy>\n      </result>\n      <result>\n        <matchFound>false</matchFound>\n        <referenceComment>CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceComment>\n        <referenceId>Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceId>\n        <wasGoodGuy>false</wasGoodGuy>\n      </result>\n    </ns2:batchMatchResponse>\n  </S:Body>\n</S:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]