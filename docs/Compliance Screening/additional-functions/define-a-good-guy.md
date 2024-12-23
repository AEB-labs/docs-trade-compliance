---
title: Define a Good Guy
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
      slug: get-compliance-profiles
      title: Get Compliance profiles
---
This request creates a Good Guy in all Good Guy lists defined in the given Compliance profile (profileIdentCode). If a Good Guy with exactly the same address fields already exists in at least one relevant Good Guy list, the Good Guy will not be created again for a second time.

See also the chapter [Match handling and Good Guys](doc:restricted-party-lists).
[block:parameters]
{
  "data": {
    "0-0": "REST",
    "1-0": "SOAP",
    "0-1": "[goodGuy](ref:goodguy-1)",
    "1-1": "<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL\" target=\"_blank\">RexBF (WSDL)</a>\n<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#defineGoodGuyWithResult-de.aeb.xnsg.rex.bf.GoodGuyAddressDTO-\" target=\"_blank\">defineGoodGuyWithResult (JavaDoc)</a>",
    "h-1": "Link to documentation",
    "h-0": "Technology"
  },
  "cols": 2,
  "rows": 2
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "In the <strong>info</strong> field, the processing comment of a user could be transferred to document the decision why the given address has been found to be a Good Guy."
}
[/block]
##Good Guys with condition
It is possible to define a Good Guy that only applies to a special context. This context is defined via  the condition. A condition could be an order number, for example.

A Good Guy without condition will always apply to all future checks of the address for which this Good Guy was defined. A Good Guy with condition “ORDER_4711” will only apply in the context of this order. Technically, this means that future checks with [Bulk address screening](doc:bulk-address-screening) or [Find matching addresses](doc:single-address-screening) of the address for which the Good Guy with condition was defined, should provide the same condition as in the Good Guy in an appropriate parameter of the request in order for this Good Guy to be applied.
[block:code]
{
  "codes": [
    {
      "code": "{\n  \"addressType\": \"company\",\n  \"name\": \"Abu Ahmed Group Inc.\",\n  \"street\": \"Fuller street 5\",\n  \"pc\": \"MK7 6AJ\",\n  \"city\": \"Manchester\",\n  \"district\": \"North\",\n  \"countryISO\": \"GB\",\n  \"telNo\": \"+4413859-489548\",\n  \"postbox\": \"12345\",\n  \"pcPostbox\": \"MK7 6AJ\",\n  \"cityPostbox\": \"Manchester\",\n  \"email\": \"abu.ahmed@google.com\",\n  \"fax\": \"+4413859-4895497\",\n  \"name1\": \"Abu Ahmed\",\n  \"name2\": \"Group Inc.\",\n  \"name3\": \"Factory for sweets of all kind\",\n  \"name4\": \"Manchester\",\n  \"title\": \"Haji\",\n  \"surname\": \"Ahmed\",\n  \"prenames\": \"Abu\",\n  \"dateOfBirth\": \"1962\",\n  \"passportData\": \"ID 385948495849\",\n  \"cityOfBirth\": \"Dublin\",\n  \"countryOfBirthISO\": \"IR\",\n  \"nationalityISO\": \"IR\",\n  \"position\": \"Senior official of the Islamic State in Iraq and the Levant (ISIL)\",\n  \"niNumber\": \"Italian fiscal code SSYBLK62T26Z336L\",\n  \"info\": \"UN Ref QDi.401\",\n  \"aliasGroupNo\": \"12345\",\n  \"free1\": \"free1\",\n  \"free2\": \"free2\",\n  \"free3\": \"free3\",\n  \"free4\": \"free4\",\n  \"free5\": \"free5\",\n  \"free6\": \"free6\",\n  \"free7\": \"free7\",\n  \"clientIdentCode\": \"APITEST\",\n  \"profileIdentCode\": \"DEFAULT\",\n  \"clientSystemId\": \"API-TEST\",\n  \"referenceId\": \"CLIENT=800;USER=BEN003;PC=PC-PHILIPP\",\n  \"referenceComment\": \"Client: 800, User: BEN003, Pc: PC-PHILIPP\",\n  \"isActive\": true,\n  \"userIdentification\": \"BEN003\",\n  \"condition\": {\n    \"value\": \"ORDER_4711\",\n    \"description\": \"Order no. 4711\"\n  }\n}",
      "language": "json"
    },
    {
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.rex.bf\">\n  <soapenv:Header/>\n  <soapenv:Body>\n    <urn:defineGoodGuyWithResult>\n      <goodGuy>\n        <addressType>?</addressType>\n        <aliasGroupNo>?</aliasGroupNo>\n        <city>?</city>\n        <cityOfBirth>?</cityOfBirth>\n        <cityPostbox>?</cityPostbox>\n        <countryISO>?</countryISO>\n        <countryOfBirthISO>?</countryOfBirthISO>\n        <dateOfBirth>?</dateOfBirth>\n        <district>?</district>\n        <email>?</email>\n        <fax>?</fax>\n        <free1>?</free1>\n        <free2>?</free2>\n        <free3>?</free3>\n        <free4>?</free4>\n        <free5>?</free5>\n        <free6>?</free6>\n        <free7>?</free7>\n        <info>?</info>\n        <name>?</name>\n        <name1>?</name1>\n        <name2>?</name2>\n        <name3>?</name3>\n        <name4>?</name4>\n        <nationalityISO>?</nationalityISO>\n        <niNumber>?</niNumber>\n        <passportData>?</passportData>\n        <pc>?</pc>\n        <pcPostbox>?</pcPostbox>\n        <position>?</position>\n        <postbox>?</postbox>\n        <prenames>?</prenames>\n        <street>?</street>\n        <surname>?</surname>\n        <telNo>?</telNo>\n        <title>?</title>\n        <clientIdentCode>?</clientIdentCode>\n        <clientSystemId>?</clientSystemId>\n        <isActive>?</isActive>\n        <profileIdentCode>?</profileIdentCode>\n        <referenceComment>?</referenceComment>\n        <referenceId>?</referenceId>\n        <userIdentification>?</userIdentification>\n        <condition>\n          <value>?</value>\n          <description>?</description>\n        </condition>\n      </goodGuy>\n    </urn:defineGoodGuyWithResult>\n  </soapenv:Body>\n</soapenv:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]