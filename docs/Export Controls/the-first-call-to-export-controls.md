---
title: The First Call to Export Controls
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
To allow you to start quickly, you will find here a complete call to do an export control check and receive a typical response.
[block:api-header]
{
  "title": "Check transaction"
}
[/block]
You can use the following example and copy/paste it into your favorite tool to test REST and/or SOAP API calls. Our test environment is prepared to work with the data in this example.	
[block:callout]
{
  "type": "info",
  "body": "To reuse this example for your login details, replace the field clientIdentCode with your client, the field profileIdentCode with your Compliance profile and the field clientSystemId with an ID for your calling system."
}
[/block]
When using REST, the URL for the request in our API test environment will be
https://rz3.aeb.de/test4ce/rest/ExportControl/v2/checkTransaction.
When using SOAP, the URL for the request in our API test environment will be
<a href="https://rz3.aeb.de:443/test4ce/servlet/bf/ExportControl40V2BF?WSDL">https://rz3.aeb.de:443/test4ce/servlet/bf/ExportControl40V2BF</a>.
[block:callout]
{
  "type": "info",
  "body": "To test REST API manually you can use this <a href=\"https://rz3.aeb.de/test4ce/swagger/#/\" target=\"_blank\">link</a> to our REST API documentation and click the \"Try it out\" button for the desired request. Do not forget to use the “Authorize” button for authentication (at the top of the web page). Otherwise, you will get a 403 HTTP error."
}
[/block]

[block:code]
{
  "codes": [
    {
      "code": "{\n\t\"clientSystemId\": \"API-TEST\",\n\t\"clientIdentCode\": \"APITEST\",\n\t\"userName\": \"BEN003\",\n\t\"resultLanguageIsoCodes\": [\n\t\t\"en\"\n\t],\n\t\"transaction\": {\n\t\t\"transactionIdHost\": \"TRANS_001\",\n\t\t\"transactionLabelHost\": \"My Order\",\n\t\t\"items\": [\n\t\t\t{\n\t\t\t\t\"itemIdHost\": \"POS_001\",\n\t\t\t\t\"itemLabelHost\": \"My first position\",\n\t\t\t\t\"partners\": [\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"CONSIGNOR_STD\",\n\t\t\t\t\t\t\"name1\": \"Exporter AG\",\n\t\t\t\t\t\t\"countryIso\": \"DE\",\n\t\t\t\t\t\t\"companyReference\": \"N012345\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"SELLER_STD\",\n\t\t\t\t\t\t\"name1\": \"Seller AG\",\n\t\t\t\t\t\t\"countryIso\": \"DE\",\n\t\t\t\t\t\t\"companyReference\": \"N0654321\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"CONSIGNEE_STD\",\n\t\t\t\t\t\t\"name1\": \"Consignee AG\",\n\t\t\t\t\t\t\"countryIso\": \"IR\",\n\t\t\t\t\t\t\"companyReference\": \"N03333\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"BUYER_STD\",\n\t\t\t\t\t\t\"name1\": \"Buyer AG\",\n\t\t\t\t\t\t\"countryIso\": \"IR\",\n\t\t\t\t\t\t\"companyReference\": \"N04444\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"ENDUSER_STD\",\n\t\t\t\t\t\t\"name1\": \"USER AG\",\n\t\t\t\t\t\t\"countryIso\": \"IR\",\n\t\t\t\t\t\t\"companyReference\": \"N02222\"\n\t\t\t\t\t}\n\t\t\t\t],\n\t\t\t\t\"decisiveDate\": \"2020-01-29T09:01:48.669Z\",\n\t\t\t\t\"productClassifications\": [\n\t\t\t\t\t{\n\t\t\t\t\t\t\"classificationIdentCode\": \"ClassificationAusfuhrliste\",\n\t\t\t\t\t\t\"classificationNumber\": \"1A001\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"classificationIdentCode\": \"CLASSIFICATION_US_EAR_CCL\",\n\t\t\t\t\t\t\"classificationNumber\": \"1A001\"\n\t\t\t\t\t}\n\t\t\t\t],\n\t\t\t\t\"valueOfGoods\": [\n\t\t\t\t\t{\n\t\t\t\t\t\t\"value\": 100000,\n\t\t\t\t\t\t\"currencyIso\": \"EUR\"\n\t\t\t\t\t}\n\t\t\t\t],\n\t\t\t\t\"orderNumber\": \"ORDER_NO12345\",\n\t\t\t\t\"quantity\": 100,\n\t\t\t\t\"quantityUnit\": \"ST\"\n\t\t\t}\n\t\t]\n\t},\n\t\"profileIdentCode\": \"DEFAULT\",\n\t\"isAutoCreateClearings\": false\n}",
      "language": "json",
      "name": "JSON"
    },
    {
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.expctrl.bf.v40\">\n   <soapenv:Header/>\n   <soapenv:Body>\n      <urn:checkTransaction>\n         <request>\n            <clientSystemId>API-TEST</clientSystemId>\n            <clientIdentCode>APITEST</clientIdentCode>\n            <userName>BEN003</userName>\n            <resultLanguageIsoCodes>en</resultLanguageIsoCodes>\n            <transaction>\n               <transactionIdHost>TRANS_001</transactionIdHost>\n               <transactionLabelHost>My Order</transactionLabelHost>\n               <items>\n                  <itemIdHost>POS_001</itemIdHost>\n                  <itemLabelHost>My first Position</itemLabelHost>\n                  <partners>\n                     <roleIdentCode>CONSIGNOR_STD</roleIdentCode>\n                     <name1>Exporter AG</name1>\n                     <countryIso>DE</countryIso>\n                     <companyReference>N012345</companyReference>\n                  </partners>\n                  <partners>\n                     <roleIdentCode>SELLER_STD</roleIdentCode>\n                     <name1>Seller AG</name1>\n                     <countryIso>DE</countryIso>\n                     <companyReference>N0654321</companyReference>\n                  </partners>\n                  <partners>\n                     <roleIdentCode>CONSIGNEE_STD</roleIdentCode>\n                     <name1>Consignee AG</name1>\n                     <countryIso>IR</countryIso>\n                     <companyReference>N03333</companyReference>\n                  </partners>\n                  <partners>\n                     <roleIdentCode>BUYER_STD</roleIdentCode>\n                     <name1>Buyer AG</name1>\n                     <countryIso>IR</countryIso>\n                     <companyReference>N04444</companyReference>\n                  </partners>\n                  <partners>\n                     <roleIdentCode>ENDUSER_STD</roleIdentCode>\n                     <name1>USER AG</name1>\n                     <countryIso>IR</countryIso>\n                     <companyReference>N02222</companyReference>\n                  </partners>\n                  <decisiveDate>2020-01-18T00:00:00+02:00</decisiveDate>\n                  <productClassifications>\n                     <classificationIdentCode>ClassificationAusfuhrliste</classificationIdentCode>\n                     <classificationNumber>1A001</classificationNumber>\n                  </productClassifications>\n                  <productClassifications>\n                     <classificationIdentCode>CLASSIFICATION_US_EAR_CCL</classificationIdentCode>\n                     <classificationNumber>1A001</classificationNumber>\n                  </productClassifications>\n                  <valueOfGoods>\n                     <value>100000</value>\n                     <currencyIso>EUR</currencyIso>\n                  </valueOfGoods>\n                  <orderNumber>ORDER_NO12345</orderNumber>\n                  <quantity>100</quantity>\n                  <quantityUnit>ST</quantityUnit>\n               </items>\n            </transaction>\n            <profileIdentCode>DEFAULT</profileIdentCode>\n            <isAutoCreateClearings>false</isAutoCreateClearings>\n         </request>\n      </urn:checkTransaction>\n   </soapenv:Body>\n</soapenv:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]
##Response
The response contains the information whether an export is allowed, something has to be done still, or the export is prohibited. See also [Results](doc:results). 
[block:code]
{
  "codes": [
    {
      "code": "{\n   \"hasErrors\": false,\n   \"hasOnlyRetryableErrors\": false,\n   \"hasWarnings\": false,\n   \"messages\": [],\n   \"totalResultType\": \"RESTRICTION\",\n   \"itemResults\": [   {\n      \"itemIdHost\": \"POS_001\",\n      \"resultType\": \"RESTRICTION\",\n      \"pluginResults\":       [\n                  {\n            \"pluginIdentCode\": \"DE-EU-Plugin\",\n            \"resultType\": \"RESTRICTION\",\n            \"clearings\": []\n         },\n                  {\n            \"pluginIdentCode\": \"US-EAR-Plugin\",\n            \"resultType\": \"RESTRICTION\",\n            \"clearings\": []\n         }\n      ]\n   }]\n}",
      "language": "json",
      "name": "JSON"
    },
    {
      "code": "<S:Envelope xmlns:S=\"http://schemas.xmlsoap.org/soap/envelope/\">\n   <S:Body>\n      <ns2:checkTransactionResponse xmlns:ns2=\"urn:de.aeb.xnsg.expctrl.bf.v40\">\n         <result>\n            <hasErrors>false</hasErrors>\n            <hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>\n            <hasWarnings>false</hasWarnings>\n            <totalResultType>RESTRICTION</totalResultType>\n            <itemResults>\n               <itemIdHost>POS_001</itemIdHost>\n               <resultType>RESTRICTION</resultType>\n               <pluginResults>\n                  <pluginIdentCode>DE-EU-Plugin</pluginIdentCode>\n                  <resultType>RESTRICTION</resultType>\n               </pluginResults>\n               <pluginResults>\n                  <pluginIdentCode>US-EAR-Plugin</pluginIdentCode>\n                  <resultType>RESTRICTION</resultType>\n               </pluginResults>\n            </itemResults>\n         </result>\n      </ns2:checkTransactionResponse>\n   </S:Body>\n</S:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]