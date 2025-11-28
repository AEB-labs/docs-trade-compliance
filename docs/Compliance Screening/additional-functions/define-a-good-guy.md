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
        [goodGuy](ref:goodguy-1)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        SOAP
      </td>

      <td style={{ textAlign: "left" }}>
        <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexBF?WSDL" target="_blank">RexBF (WSDL)</a>\ <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#defineGoodGuyWithResult-de.aeb.xnsg.rex.bf.GoodGuyAddressDTO-" target="_blank">defineGoodGuyWithResult (JavaDoc)</a>
      </td>
    </tr>
  </tbody>
</Table>

> 📘 In the <strong>info</strong> field, the processing comment of a user could be transferred to document the decision why the given address has been found to be a Good Guy.

## Good Guys with condition

It is possible to define a Good Guy that only applies to a special context. This context is defined via  the condition. A condition could be an order number, for example.

A Good Guy without condition will always apply to all future checks of the address for which this Good Guy was defined. A Good Guy with condition “ORDER\_4711” will only apply in the context of this order. Technically, this means that future checks with [Bulk address screening](doc:bulk-address-screening) or [Find matching addresses](doc:single-address-screening) of the address for which the Good Guy with condition was defined, should provide the same condition as in the Good Guy in an appropriate parameter of the request in order for this Good Guy to be applied.

```json
{
  "addressType": "company",
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
  "clientIdentCode": "APITEST",
  "profileIdentCode": "DEFAULT",
  "clientSystemId": "API-TEST",
  "referenceId": "CLIENT=800;USER=BEN003;PC=PC-PHILIPP",
  "referenceComment": "Client: 800, User: BEN003, Pc: PC-PHILIPP",
  "isActive": true,
  "userIdentification": "BEN003",
  "condition": {
    "value": "ORDER_4711",
    "description": "Order no. 4711"
  }
}
```
```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.rex.bf">
  <soapenv:Header/>
  <soapenv:Body>
    <urn:defineGoodGuyWithResult>
      <goodGuy>
        <addressType>?</addressType>
        <aliasGroupNo>?</aliasGroupNo>
        <city>?</city>
        <cityOfBirth>?</cityOfBirth>
        <cityPostbox>?</cityPostbox>
        <countryISO>?</countryISO>
        <countryOfBirthISO>?</countryOfBirthISO>
        <dateOfBirth>?</dateOfBirth>
        <district>?</district>
        <email>?</email>
        <fax>?</fax>
        <free1>?</free1>
        <free2>?</free2>
        <free3>?</free3>
        <free4>?</free4>
        <free5>?</free5>
        <free6>?</free6>
        <free7>?</free7>
        <info>?</info>
        <name>?</name>
        <name1>?</name1>
        <name2>?</name2>
        <name3>?</name3>
        <name4>?</name4>
        <nationalityISO>?</nationalityISO>
        <niNumber>?</niNumber>
        <passportData>?</passportData>
        <pc>?</pc>
        <pcPostbox>?</pcPostbox>
        <position>?</position>
        <postbox>?</postbox>
        <prenames>?</prenames>
        <street>?</street>
        <surname>?</surname>
        <telNo>?</telNo>
        <title>?</title>
        <clientIdentCode>?</clientIdentCode>
        <clientSystemId>?</clientSystemId>
        <isActive>?</isActive>
        <profileIdentCode>?</profileIdentCode>
        <referenceComment>?</referenceComment>
        <referenceId>?</referenceId>
        <userIdentification>?</userIdentification>
        <condition>
          <value>?</value>
          <description>?</description>
        </condition>
      </goodGuy>
    </urn:defineGoodGuyWithResult>
  </soapenv:Body>
</soapenv:Envelope>
```
