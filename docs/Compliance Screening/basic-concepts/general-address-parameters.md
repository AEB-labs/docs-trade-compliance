---
title: Address Fields
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
## Check-Relevant Address Fields

An address check request should at least contain a name. The compliance profile used determines for which name or names an address check is performed. First, a so-called name block is checked, which can either be the name explicitly passed in the field "name", or a combination of any of the fields "name1" to "name4", as configured in the compliance profile. If the configured combination of "name1" to "name4" is empty, the field "name" will still be checked as a fallback. 

In addition to the check of the name block, an additional separate check for each of the fields "name1" to "name4" can also be configured in the compliance profile. For further details, please refer to the help for your compliance profile setting in the web application and [Basic concepts](https://dash.readme.com/project/trade-compliance/v4.0/docs/basic-concepts-1).

The fields "addressType", "street", "pc", "postbox", "city" and "country" are optional, but contribute to the accuracy of the check. It is recommended to always fill these fields - if the data is available - to make the check more precise.

An additional ID-only check can be configured in the compliance profile (if ID check is activated globally for an installation). If the ID-only check is activated, IDs (e.g., DUNS number, tax number) transmitted in the address check request will be used to perform an additional check for matching IDs, in addition to the check of name and address. The prerequisite for a meaningful check for IDs is that the restricted party lists you check against also contain these IDs. Currently, IDs are only available in Dow Jones content and possibly in manually created restricted party lists.

```json
{
  "addresses": [
    {
      "addressType": "entity",
      "name": "Abu Ahmed Group Inc.",
      "referenceId": "CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP"
    },
    {
      "addressType": "individual",
      "name": "John Doe",
      "name1": "John",
      "name2": "not Existing",
      "name3": "Doe",
      "street": "Example Street 123",
      "pc": "12345",
      "city": "Example City",
      "countryISO": "DE",
      "referenceId": "CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP",
      "referenceComment": "Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP"
    }
  ],
  "screeningParameters": {
    "clientIdentCode": "APITEST",
    "profileIdentCode": "DEFAULT",
    "clientSystemId": "API-TEST",
    "userIdentification": "BEN003",
    "addressTypeVersion": "1"
  }
}
```
```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.rex.bf">
  <soapenv:Header/>
  <soapenv:Body>
    <urn:batchMatch>
      <patterns>
        <addressType>entity</addressType>
        <name>Abu Ahmed Group Inc.</name>
        <referenceComment>CUSNO=4711;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceComment>
      </patterns>
      <patterns>
        <addressType>individual</addressType>
        <name>John Doe</name>
        <name1>John</name1>
        <name2>not Existing</name2>
        <name3>Doe</name3>
      	<street>Example Street 123</street>
        <pc>12345</pc>
        <city>Example City</city>
      	<countryISO>DE</countryISO>
      	<referenceId>CUSNO=4712;CLIENT=800;USER=BEN003;PC=PC-PHILIPP</referenceId>
      	<referenceComment>Customer no.: 4712, Client: 800, User: BEN003, Pc: PC-PHILIPP</referenceComment>
      </patterns>
      <parms>
        <clientIdentCode>APITEST</clientIdentCode>
        <profileIdentCode>DEFAULT</profileIdentCode>
        <clientSystemId>API-TEST</clientSystemId>
        <userIdentification>BEN003</userIdentification>
        <addressTypeVersion>1</addressTypeVersion>
      </parms>
    </urn:batchMatch>
  </soapenv:Body>
</soapenv:Envelope>
```

> 📘 ADDRESS\_TYPE\_VERSION
>
> The field "addressTypeVersion" determines the address types that can be used in an address check. The current standard is ADDRESS\_TYPE\_VERSION\_1. This version corresponds to the typical qualification of sanction list addresses and should always be used.
>
> ADDRESS\_TYPE\_VERSION\_0 is currently only supported to ensure backward compatibility.

## Additional Address Fields

In addition to the address fields described above, which are relevant for the address comparison, you will also find fields that are purely informative. These include the fields "title", "surname", "prenames", "telNo", "district", "email", "position", "info" and "free1" to "free7". These parameters are not relevant for the address comparison itself, but can provide useful meta-information for your users when analysing an address match or defining a good guy.

The field "referenceId" is intended for internal, technical use. It can be used to to build references between the compliance protocols and the client system.
