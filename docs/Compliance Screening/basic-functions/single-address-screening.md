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
        [findMatchingAddresses](ref:findmatchingaddresses)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        SOAP
      </td>

      <td style={{ textAlign: "left" }}>
        <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL" target="_blank">RexBF (WSDL)</a>\ <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getMatchingAddresses-de.aeb.xnsg.rex.bf.AddressPatternDTO-de.aeb.xnsg.rex.bf.MatchParametersDTO-" target="_blank">getMatchingAddresses (JavaDoc)</a>
      </td>
    </tr>
  </tbody>
</Table>

## Example Request

```json
{
  "address": {
    "addressType": "entity",
    "name": "Abu Ahmed Group Inc.",
    "street": "Fuller street 5",
    "pc": "MK7 6AJ",
    "city": "Manchester",
    "district": "North",
    "countryISO": "GB",
    "telNo": "+4413859-489548",
    "postbox": "12345",
    "pcPostbox": "MK7 6AJ",
    "cityPostbox": "Manchester",
    "email": "abu.ahmed@google.com",
    "fax": "+4413859-4895497",
    "name1": "Abu Ahmed",
    "name2": "Group Inc.",
    "name3": "Factory for sweets of all kind",
    "name4": "Manchester",
    "title": "Haji",
    "surname": "Ahmed",
    "prenames": "Abu",
    "dateOfBirth": "1962",
    "passportData": "ID 385948495849",
    "cityOfBirth": "Dublin",
    "countryOfBirthISO": "IR",
    "nationalityISO": "IR",
    "position": "Senior official of the Islamic State in Iraq and the Levant (ISIL)",
    "niNumber": "Italian fiscal code SSYBLK62T26Z336L",
    "info": "UN Ref QDi.401",
    "aliasGroupNo": "12345",
    "free1": "free1",
    "free2": "free2",
    "free3": "free3",
    "free4": "free4",
    "free5": "free5",
    "free6": "free6",
    "free7": "free7",
    "referenceId": "CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP",
    "referenceComment": "Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP",
    "condition": {
      "value": "ORDER_12345",
      "description": "Order no. 12345"
    }
  },
  "screeningParameters": {
    "clientIdentCode": "APITEST",
    "profileIdentCode": "DEFAULT",
    "threshold": 60,
    "clientSystemId": "API-TEST",
    "suppressLogging": true,
    "considerGoodGuys": true,
    "userIdentification": "BEN003",
    "addressTypeVersion": "1"
  }
}
```
```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.rex.bf">
  <soapenv:Header/>
  <soapenv:Body>
    <urn:getMatchingAddresses>
      <pattern>
        <addressType>entity</addressType>
        <aliasGroupNo>12345</aliasGroupNo>
        <city>Manchester</city>
        <cityOfBirth>Dublin</cityOfBirth>
        <cityPostbox>Manchester</cityPostbox>
        <countryISO>GB</countryISO>
        <countryOfBirthISO>IR</countryOfBirthISO>
        <dateOfBirth>1962</dateOfBirth>
        <district>North</district>
        <email>abu.ahmed@google.com</email>
        <fax>+4413859-4895497</fax>
        <free1>free1</free1>
        <free2>free2</free2>
        <free3>free3</free3>
        <free4>free4</free4>
        <free5>free5</free5>
        <free6>free6</free6>
        <free7>free7</free7>
        <info>UN Ref QDi.401</info>
        <name>Abu Ahmed Group Inc.</name>
        <name1>Abu Ahmed</name1>
        <name2>Group Inc.</name2>
        <name3>Factory for sweets of all kind</name3>
        <name4>Manchester</name4>
        <nationalityISO>IR</nationalityISO>
        <niNumber>Italian fiscal code SSYBLK62T26Z336L</niNumber>
        <passportData>ID 385948495849</passportData>
        <pc>MK7 6AJ</pc>
        <pcPostbox>MK7 6AJ</pcPostbox>
        <position>Senior official of the Islamic State in Iraq and the Levant (ISIL)</position>
        <postbox>12345</postbox>
        <prenames>Abu</prenames>
        <street>Fuller street 5</street>
        <surname>Ahmed</surname>
        <telNo>+4413859-489548</telNo>
        <title>Haji</title>
        <referenceComment>Customer no.: 4711, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceComment>
        <referenceId>CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceId>
        <condition>
          <value>ORDER_12345</value>
          <description>Order no. 12345</description>
        </condition>
      </pattern>
      <parms>
        <checkType></checkType>
        <clientIdentCode>APITEST</clientIdentCode>
        <clientSystemId>API-TEST</clientSystemId>
        <considerGoodGuys>true</considerGoodGuys>
        <profileIdentCode>DEFAULT</profileIdentCode>
        <threshold>60</threshold>
        <suppressLogging>true</suppressLogging>
        <userIdentification>BEN003</userIdentification>
        <addressTypeVersion>1</addressTypeVersion>
      </parms>
    </urn:getMatchingAddresses>
  </soapenv:Body>
</soapenv:Envelope>
```

## Example Response

```json
[
  {
    "addressType": "entity",
    "name": "Abu Ahmed Group Inc.",
    "street": "Fuller street 5",
    "pc": "MK7 6AJ",
    "city": "Manchester",
    "district": "North",
    "countryISO": "GB",
    "telNo": "+4413859-489548",
    "postbox": "12345",
    "pcPostbox": "MK7 6AJ",
    "cityPostbox": "Manchester",
    "email": "abu.ahmed@google.com",
    "fax": "+4413859-4895497",
    "name1": "Abu Ahmed",
    "name2": "Group Inc.",
    "name3": "Factory for sweets of all kind",
    "name4": "Manchester",
    "title": "Haji",
    "surname": "Ahmed",
    "prenames": "Abu",
    "dateOfBirth": "1962",
    "passportData": "ID 385948495849",
    "cityOfBirth": "Dublin",
    "countryOfBirthISO": "IR",
    "nationalityISO": "IR",
    "position": "Senior official of the Islamic State in Iraq and the Levant (ISIL)",
    "niNumber": "Italian fiscal code SSYBLK62T26Z336L",
    "info": "UN Ref QDi.401",
    "aliasGroupNo": "12345",
    "free1": "free1",
    "free2": "free2",
    "free3": "free3",
    "free4": "free4",
    "free5": "free5",
    "free6": "free6",
    "free7": "free7",
    "similarity": 85,
    "listAbbreviation": "FRNL",
    "listName": "UK - Consolidated List of Financial Sanctions Targets in the UK",
    "listGroupName": "BOE",
    "internalAddressId": "12345678901234567890",
    "restrictionType": "EU-CR",
    "restrictionSource": "Terrorism and Terrorist Financing",
    "restrictionDate": "2020-09-16T15:00:25.566Z",
    "sourceWebLink": "www.youm7.com/story/2017/6/9/",
    "hasMoreDetails": true,
    "matchType": "ADDRESS_AND_NAME",
    "embargoArea": "someAreaName"
  }
]
```
```xml XML (SOAP)
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
   <S:Body>
      <ns2:getMatchingAddressesResponse xmlns:ns2="urn:de.aeb.xnsg.rex.bf">
         <result>
            <addressType>entity</addressType>
            <aliasGroupNo>12345</aliasGroupNo>
            <city>Manchester</city>
            <cityOfBirth>Dublin</cityOfBirth>
            <cityPostbox>Manchester</cityPostbox>
            <countryISO>GB</countryISO>
            <countryOfBirthISO>IR</countryOfBirthISO>
            <dateOfBirth>1962</dateOfBirth>
            <district>North</district>
            <email>abu.ahmed@google.com</email>
            <fax>+4413859-4895497</fax>
            <free1>free1</free1>
            <free2>free2</free2>
            <free3>free3</free3>
            <free4>free4</free4>
            <free5>free5</free5>
            <free6>free6</free6>
            <free7>free7</free7>
            <info>UN Ref QDi.401</info>
            <name>Abu Ahmed Group Inc.</name>
            <name1>Abu Ahmed</name1>
            <name2>Group Inc.</name2>
            <name3>Factory for sweets of all kind</name3>
            <name4>Manchester</name4>
            <nationalityISO>IR</nationalityISO>
            <niNumber>Italian fiscal code SSYBLK62T26Z336L</niNumber>
            <passportData>ID 385948495849</passportData>
            <pc>MK7 6AJ</pc>
            <pcPostbox>MK7 6AJ</pcPostbox>
            <position>Senior official of the Islamic State in Iraq and the Levant (ISIL)</position>
            <postbox>12345</postbox>
            <prenames>Abu</prenames>
            <street>Fuller street 5</street>
            <surname>Ahmed</surname>
            <telNo>+4413859-489548</telNo>
            <title>Haji</title>
            <embargoArea>SomeAreaName</embargoArea>
            <internalAddressId>12345678901234567890</internalAddressId>
            <listGroupName>BOE</listGroupName>
            <listAbbreviation>FRNL</listAbbreviation>
            <listName>UK - Consolidated List of Financial Sanctions Targets in the UK</listName>
            <restrictionDate>2020-09-16T15:00:25.566Z</restrictionDate>
            <restrictionSource>Terrorism and Terrorist Financing</restrictionSource>
            <restrictionType>EU-CR</restrictionType>
            <similarity>85</similarity>
            <sourceWebLink>www.youm7.com/story/2017/6/9/</sourceWebLink>
            <hasMoreDetails>true</hasMoreDetails>
            <matchType>ADDRESS_AND_NAME</matchType>
         </result>
      </ns2:getMatchingAddressesResponse>
   </S:Body>
</S:Envelope>
```
