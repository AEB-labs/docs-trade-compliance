---
title: Bulk Address Screening
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
      slug: single-address-screening
      title: Find matching addresses
---
The main request of Compliance Screening API is bulk address screening. This works for single addresses and for larger amounts of addresses as well. See also the chapter [Bulk vs single address screening](doc:bulk-vs-single-address-screening).
[block:parameters]
{
  "data": {
    "0-0": "REST",
    "1-0": "SOAP",
    "0-1": "[screenAddresses](ref:screenaddresses)",
    "1-1": "<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL\" target=\"_blank\">RexBF (WSDL)</a>\n<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#batchMatch-de.aeb.xnsg.rex.bf.AddressPatternDTO:A-de.aeb.xnsg.rex.bf.MatchParametersDTO-\" target=\"_blank\">batchMatch (JavaDoc)</a>",
    "h-1": "Link to documentation",
    "h-0": "Technology"
  },
  "cols": 2,
  "rows": 2
}
[/block]
##Screening of addresses from master data
Usually, it is necessary to periodically screen all addresses which are part of the master data (e.g. customers, suppliers, or employees), e.g. once every night or once a week. You may have several thousand of such addresses, so performance is important. For this reason, there is a bulk screening request which allows you to screen multiple addresses with one call. 

Processing too large amounts of addresses with one call can lead to timeouts, depending on the server and system configuration. A typical batch size could be 100 addresses. However, if you plan to use very big restricted party lists (e.g. from Dow Jones), it may be neccessary to choose smaller block sizes to get acceptable response times.
[block:callout]
{
  "type": "warning",
  "body": "For performance reasons, it is not allowed to perform parallel calls of bulk address screening. However, if you absolutely need parallel calls, please contact AEB because in this case the system environment should be configured accordingly."
}
[/block]
The response of a bulk address screening request contains the overall result of the address check for each address (if there were any matches found or not). Address checks also create log entries in Trade Compliance Management which can be accessed there. Logs include further details about matches like all the matching restricted party addresses found. The logs are also used for the match handling of address matches in Trade Compliance Management, i.e. definition of good guys, etc.

[block:callout]
{
  "type": "info",
  "body": "If *suppressLogging* is set to 'true', no logs will be created and match handling in Trade Compliance Management will not be possible."
}
[/block]
##Screening of transaction data
If it is needed to screen transaction data (e.g. orders, deliveries) which also contain typically more than one address (e.g. customer, consignee, forwarder), you should perform a bulk address screening at an appropriate point in time (e.g. shortly before confirming an order or picking a delivery).

##Example Request
[block:code]
{
  "codes": [
    {
      "code": "{\n  \"addresses\": [\n    {\n      \"addressType\": \"entity\",\n      \"name\": \"Abu Ahmed Group Inc.\",\n      \"street\": \"Fuller street 5\",\n      \"pc\": \"MK7 6AJ\",\n      \"city\": \"Manchester\",\n      \"district\": \"North\",\n      \"countryISO\": \"GB\",\n      \"telNo\": \"+4413859-489548\",\n      \"postbox\": \"12345\",\n      \"pcPostbox\": \"MK7 6AJ\",\n      \"cityPostbox\": \"Manchester\",\n      \"email\": \"abu.ahmed@google.com\",\n      \"fax\": \"+4413859-4895497\",\n      \"name1\": \"Abu Ahmed\",\n      \"name2\": \"Group Inc.\",\n      \"name3\": \"Factory for sweets of all kind\",\n      \"name4\": \"Manchester\",\n      \"title\": \"Haji\",\n      \"surname\": \"Ahmed\",\n      \"prenames\": \"Abu\",\n      \"dateOfBirth\": \"1962\",\n      \"passportData\": \"ID 385948495849\",\n      \"cityOfBirth\": \"Dublin\",\n      \"countryOfBirthISO\": \"IR\",\n      \"nationalityISO\": \"IR\",\n      \"position\": \"Senior official of the Islamic State in Iraq and the Levant (ISIL)\",\n      \"niNumber\": \"Italian fiscal code SSYBLK62T26Z336L\",\n      \"info\": \"UN Ref QDi.401\",\n      \"aliasGroupNo\": \"12345\",\n      \"free1\": \"free1\",\n      \"free2\": \"free2\",\n      \"free3\": \"free3\",\n      \"free4\": \"free4\",\n      \"free5\": \"free5\",\n      \"free6\": \"free6\",\n      \"free7\": \"free7\",\n      \"referenceId\": \"CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP\",\n      \"referenceComment\": \"Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP\",\n      \"condition\": {\n        \"value\": \"ORDER_12345\",\n        \"description\": \"Order no. 12345\"\n      }\n    }\n  ],\n  \"screeningParameters\": {\n    \"clientIdentCode\": \"APITEST\",\n    \"profileIdentCode\": \"DEFAULT\",\n    \"threshold\": 60,\n    \"clientSystemId\": \"API-TEST\",\n    \"suppressLogging\": false,\n    \"considerGoodGuys\": true,\n    \"userIdentification\": \"BEN003\",\n    \"addressTypeVersion\": \"1\"\n  }\n}",
      "language": "json"
    },
    {
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.rex.bf\">\n  <soapenv:Header/>\n  <soapenv:Body>\n      <urn:batchMatch>\n         <patterns>\n            <addressType>entity</addressType>\n            <aliasGroupNo>12345</aliasGroupNo>\n            <city>Manchester</city>\n            <cityOfBirth>Dublin</cityOfBirth>\n            <cityPostbox>Manchester</cityPostbox>\n            <countryISO>GB</countryISO>\n            <countryOfBirthISO>IR</countryOfBirthISO>\n            <dateOfBirth>1962</dateOfBirth>\n            <district>North</district>\n            <email>abu.ahmed@google.com</email>\n            <fax>+4413859-4895497</fax>\n            <free1>free1</free1>\n            <free2>free2</free2>\n            <free3>free3</free3>\n            <free4>free4</free4>\n            <free5>free5</free5>\n            <free6>free6</free6>\n            <free7>free7</free7>\n            <info>UN Ref QDi.401</info>\n            <name>Abu Ahmed Group Inc.</name>\n            <name1>Abu Ahmed</name1>\n            <name2>Group Inc.</name2>\n            <name3>Factory for sweets of all kind</name3>\n            <name4>Manchester</name4>\n            <nationalityISO>IR</nationalityISO>\n            <niNumber>Italian fiscal code SSYBLK62T26Z336L</niNumber>\n            <passportData>ID 385948495849</passportData>\n            <pc>MK7 6AJ</pc>\n            <pcPostbox>MK7 6AJ</pcPostbox>\n            <position>Senior official of the Islamic State in Iraq and the Levant (ISIL)</position>\n            <postbox>12345</postbox>\n            <prenames>Abu</prenames>\n            <street>Fuller street 5</street>\n            <surname>Ahmed</surname>\n            <telNo>+4413859-489548</telNo>\n            <title>Haji</title>\n            <referenceComment>Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceComment>\n            <referenceId>CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceId>\n            <condition>\n               <value>ORDER_12345</value>\n               <description>Order no. 12345</description>\n            </condition>\n         </patterns>\n         <parms>\n            <checkType></checkType>\n            <clientIdentCode>APITEST</clientIdentCode>\n            <clientSystemId>API-TEST</clientSystemId>\n            <considerGoodGuys>true</considerGoodGuys>\n            <profileIdentCode>DEFAULT</profileIdentCode>\n            <threshold>60</threshold>\n            <suppressLogging>false</suppressLogging>\n            <userIdentification>BEN003</userIdentification>\n            <addressTypeVersion>1</addressTypeVersion>\n         </parms>\n      </urn:batchMatch>\n   </soapenv:Body>\n</soapenv:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]
##Example Response
[block:code]
{
  "codes": [
    {
      "code": "[\n  {\n    \"matchFound\": true,\n    \"wasGoodGuy\": false,\n    \"referenceId\": \"CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP\",\n    \"referenceComment\": \"Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP\"\n  }\n]",
      "language": "json"
    },
    {
      "code": "<S:Envelope xmlns:S=\"http://schemas.xmlsoap.org/soap/envelope/\">\n   <S:Body>\n      <ns2:batchMatchResponse xmlns:ns2=\"urn:de.aeb.xnsg.rex.bf\">\n         <result>\n            <matchFound>true</matchFound>\n            <referenceComment>Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceComment>\n            <referenceId>CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceId>\n            <wasGoodGuy>false</wasGoodGuy>\n         </result>\n      </ns2:batchMatchResponse>\n   </S:Body>\n</S:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]