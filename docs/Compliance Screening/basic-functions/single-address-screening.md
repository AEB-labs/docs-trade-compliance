---
title: Find Matching Addresses
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
      slug: define-a-good-guy
      title: Define a Good Guy
---
This request finds all restricted party addresses matching a given address.

In most cases, this request is used for handling matches found via [Bulk address screening](doc:bulk-address-screening). It is used to display matching restricted party addresses of a checked address to the user who needs to decide if the addresses found are real matches or not.

See also the chapters [Bulk vs single address screening](doc:bulk-vs-single-address-screening) and [Match handling and Good Guys](doc:restricted-party-lists).
[block:parameters]
{
  "data": {
    "0-0": "REST",
    "1-0": "SOAP",
    "0-1": "[findMatchingAddresses](ref:findmatchingaddresses)",
    "1-1": "<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL\" target=\"_blank\">RexBF (WSDL)</a>\n<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getMatchingAddresses-de.aeb.xnsg.rex.bf.AddressPatternDTO-de.aeb.xnsg.rex.bf.MatchParametersDTO-\" target=\"_blank\">getMatchingAddresses (JavaDoc)</a>",
    "h-0": "Technology",
    "h-1": "Link to documentation"
  },
  "cols": 2,
  "rows": 2
}
[/block]
##Example Request
[block:code]
{
  "codes": [
    {
      "code": "{\n  \"address\": {\n    \"addressType\": \"entity\",\n    \"name\": \"Abu Ahmed Group Inc.\",\n    \"street\": \"Fuller street 5\",\n    \"pc\": \"MK7 6AJ\",\n    \"city\": \"Manchester\",\n    \"district\": \"North\",\n    \"countryISO\": \"GB\",\n    \"telNo\": \"+4413859-489548\",\n    \"postbox\": \"12345\",\n    \"pcPostbox\": \"MK7 6AJ\",\n    \"cityPostbox\": \"Manchester\",\n    \"email\": \"abu.ahmed@google.com\",\n    \"fax\": \"+4413859-4895497\",\n    \"name1\": \"Abu Ahmed\",\n    \"name2\": \"Group Inc.\",\n    \"name3\": \"Factory for sweets of all kind\",\n    \"name4\": \"Manchester\",\n    \"title\": \"Haji\",\n    \"surname\": \"Ahmed\",\n    \"prenames\": \"Abu\",\n    \"dateOfBirth\": \"1962\",\n    \"passportData\": \"ID 385948495849\",\n    \"cityOfBirth\": \"Dublin\",\n    \"countryOfBirthISO\": \"IR\",\n    \"nationalityISO\": \"IR\",\n    \"position\": \"Senior official of the Islamic State in Iraq and the Levant (ISIL)\",\n    \"niNumber\": \"Italian fiscal code SSYBLK62T26Z336L\",\n    \"info\": \"UN Ref QDi.401\",\n    \"aliasGroupNo\": \"12345\",\n    \"free1\": \"free1\",\n    \"free2\": \"free2\",\n    \"free3\": \"free3\",\n    \"free4\": \"free4\",\n    \"free5\": \"free5\",\n    \"free6\": \"free6\",\n    \"free7\": \"free7\",\n    \"referenceId\": \"CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP\",\n    \"referenceComment\": \"Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP\",\n    \"condition\": {\n      \"value\": \"ORDER_12345\",\n      \"description\": \"Order no. 12345\"\n    }\n  },\n  \"screeningParameters\": {\n    \"clientIdentCode\": \"APITEST\",\n    \"profileIdentCode\": \"DEFAULT\",\n    \"threshold\": 60,\n    \"clientSystemId\": \"API-TEST\",\n    \"suppressLogging\": true,\n    \"considerGoodGuys\": true,\n    \"userIdentification\": \"BEN003\",\n    \"addressTypeVersion\": \"1\"\n  }\n}",
      "language": "json"
    },
    {
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.rex.bf\">\n  <soapenv:Header/>\n  <soapenv:Body>\n    <urn:getMatchingAddresses>\n      <pattern>\n        <addressType>entity</addressType>\n        <aliasGroupNo>12345</aliasGroupNo>\n        <city>Manchester</city>\n        <cityOfBirth>Dublin</cityOfBirth>\n        <cityPostbox>Manchester</cityPostbox>\n        <countryISO>GB</countryISO>\n        <countryOfBirthISO>IR</countryOfBirthISO>\n        <dateOfBirth>1962</dateOfBirth>\n        <district>North</district>\n        <email>abu.ahmed@google.com</email>\n        <fax>+4413859-4895497</fax>\n        <free1>free1</free1>\n        <free2>free2</free2>\n        <free3>free3</free3>\n        <free4>free4</free4>\n        <free5>free5</free5>\n        <free6>free6</free6>\n        <free7>free7</free7>\n        <info>UN Ref QDi.401</info>\n        <name>Abu Ahmed Group Inc.</name>\n        <name1>Abu Ahmed</name1>\n        <name2>Group Inc.</name2>\n        <name3>Factory for sweets of all kind</name3>\n        <name4>Manchester</name4>\n        <nationalityISO>IR</nationalityISO>\n        <niNumber>Italian fiscal code SSYBLK62T26Z336L</niNumber>\n        <passportData>ID 385948495849</passportData>\n        <pc>MK7 6AJ</pc>\n        <pcPostbox>MK7 6AJ</pcPostbox>\n        <position>Senior official of the Islamic State in Iraq and the Levant (ISIL)</position>\n        <postbox>12345</postbox>\n        <prenames>Abu</prenames>\n        <street>Fuller street 5</street>\n        <surname>Ahmed</surname>\n        <telNo>+4413859-489548</telNo>\n        <title>Haji</title>\n        <referenceComment>Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceComment>\n        <referenceId>CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceId>\n        <condition>\n          <value>ORDER_12345</value>\n          <description>Order no. 12345</description>\n        </condition>\n      </pattern>\n      <parms>\n        <checkType></checkType>\n        <clientIdentCode>APITEST</clientIdentCode>\n        <clientSystemId>API-TEST</clientSystemId>\n        <considerGoodGuys>true</considerGoodGuys>\n        <profileIdentCode>DEFAULT</profileIdentCode>\n        <threshold>60</threshold>\n        <suppressLogging>true</suppressLogging>\n        <userIdentification>BEN003</userIdentification>\n        <addressTypeVersion>1</addressTypeVersion>\n      </parms>\n    </urn:getMatchingAddresses>\n  </soapenv:Body>\n</soapenv:Envelope>",
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
      "code": "[\n  {\n    \"addressType\": \"entity\",\n    \"name\": \"Abu Ahmed Group Inc.\",\n    \"street\": \"Fuller street 5\",\n    \"pc\": \"MK7 6AJ\",\n    \"city\": \"Manchester\",\n    \"district\": \"North\",\n    \"countryISO\": \"GB\",\n    \"telNo\": \"+4413859-489548\",\n    \"postbox\": \"12345\",\n    \"pcPostbox\": \"MK7 6AJ\",\n    \"cityPostbox\": \"Manchester\",\n    \"email\": \"abu.ahmed@google.com\",\n    \"fax\": \"+4413859-4895497\",\n    \"name1\": \"Abu Ahmed\",\n    \"name2\": \"Group Inc.\",\n    \"name3\": \"Factory for sweets of all kind\",\n    \"name4\": \"Manchester\",\n    \"title\": \"Haji\",\n    \"surname\": \"Ahmed\",\n    \"prenames\": \"Abu\",\n    \"dateOfBirth\": \"1962\",\n    \"passportData\": \"ID 385948495849\",\n    \"cityOfBirth\": \"Dublin\",\n    \"countryOfBirthISO\": \"IR\",\n    \"nationalityISO\": \"IR\",\n    \"position\": \"Senior official of the Islamic State in Iraq and the Levant (ISIL)\",\n    \"niNumber\": \"Italian fiscal code SSYBLK62T26Z336L\",\n    \"info\": \"UN Ref QDi.401\",\n    \"aliasGroupNo\": \"12345\",\n    \"free1\": \"free1\",\n    \"free2\": \"free2\",\n    \"free3\": \"free3\",\n    \"free4\": \"free4\",\n    \"free5\": \"free5\",\n    \"free6\": \"free6\",\n    \"free7\": \"free7\",\n    \"similarity\": 85,\n    \"listAbbreviation\": \"FRNL\",\n    \"listName\": \"UK - Consolidated List of Financial Sanctions Targets in the UK\",\n    \"listGroupName\": \"BOE\",\n    \"internalAddressId\": \"12345678901234567890\",\n    \"restrictionType\": \"EU-CR\",\n    \"restrictionSource\": \"Terrorism and Terrorist Financing\",\n    \"restrictionDate\": \"2020-09-16T15:00:25.566Z\",\n    \"sourceWebLink\": \"www.youm7.com/story/2017/6/9/\",\n    \"hasMoreDetails\": true,\n    \"matchType\": \"ADDRESS_AND_NAME\",\n    \"embargoArea\": \"someAreaName\"\n  }\n]",
      "language": "json"
    },
    {
      "code": "<S:Envelope xmlns:S=\"http://schemas.xmlsoap.org/soap/envelope/\">\n   <S:Body>\n      <ns2:getMatchingAddressesResponse xmlns:ns2=\"urn:de.aeb.xnsg.rex.bf\">\n         <result>\n            <addressType>entity</addressType>\n            <aliasGroupNo>12345</aliasGroupNo>\n            <city>Manchester</city>\n            <cityOfBirth>Dublin</cityOfBirth>\n            <cityPostbox>Manchester</cityPostbox>\n            <countryISO>GB</countryISO>\n            <countryOfBirthISO>IR</countryOfBirthISO>\n            <dateOfBirth>1962</dateOfBirth>\n            <district>North</district>\n            <email>abu.ahmed@google.com</email>\n            <fax>+4413859-4895497</fax>\n            <free1>free1</free1>\n            <free2>free2</free2>\n            <free3>free3</free3>\n            <free4>free4</free4>\n            <free5>free5</free5>\n            <free6>free6</free6>\n            <free7>free7</free7>\n            <info>UN Ref QDi.401</info>\n            <name>Abu Ahmed Group Inc.</name>\n            <name1>Abu Ahmed</name1>\n            <name2>Group Inc.</name2>\n            <name3>Factory for sweets of all kind</name3>\n            <name4>Manchester</name4>\n            <nationalityISO>IR</nationalityISO>\n            <niNumber>Italian fiscal code SSYBLK62T26Z336L</niNumber>\n            <passportData>ID 385948495849</passportData>\n            <pc>MK7 6AJ</pc>\n            <pcPostbox>MK7 6AJ</pcPostbox>\n            <position>Senior official of the Islamic State in Iraq and the Levant (ISIL)</position>\n            <postbox>12345</postbox>\n            <prenames>Abu</prenames>\n            <street>Fuller street 5</street>\n            <surname>Ahmed</surname>\n            <telNo>+4413859-489548</telNo>\n            <title>Haji</title>\n            <embargoArea>SomeAreaName</embargoArea>\n            <internalAddressId>12345678901234567890</internalAddressId>\n            <listGroupName>BOE</listGroupName>\n            <listAbbreviation>FRNL</listAbbreviation>\n            <listName>UK - Consolidated List of Financial Sanctions Targets in the UK</listName>\n            <restrictionDate>2020-09-16T15:00:25.566Z</restrictionDate>\n            <restrictionSource>Terrorism and Terrorist Financing</restrictionSource>\n            <restrictionType>EU-CR</restrictionType>\n            <similarity>85</similarity>\n            <sourceWebLink>www.youm7.com/story/2017/6/9/</sourceWebLink>\n            <hasMoreDetails>true</hasMoreDetails>\n            <matchType>ADDRESS_AND_NAME</matchType>\n         </result>\n      </ns2:getMatchingAddressesResponse>\n   </S:Body>\n</S:Envelope>\n",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]