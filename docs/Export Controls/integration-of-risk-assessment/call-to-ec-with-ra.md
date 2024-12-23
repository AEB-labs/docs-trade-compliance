---
title: The First Call to Export Controls with RA integration
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
To allow you to start quickly, you will find here a complete call to do an Export Control check with Risk Assessment integration and receive a typical response.
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
      "code": "{\n\t\"clientSystemId\": \"API-TEST\",\n\t\"clientIdentCode\": \"APITEST\",\n\t\"userName\": \"BEN003\",\n\t\"resultLanguageIsoCodes\": [\n\t\t\"en\"\n\t],\n\t\"transaction\": {\n\t\t\"transactionIdHost\": \"TRANS_002\",\n\t\t\"transactionLabelHost\": \"My 2nd Order\",\n\t\t\"items\": [\n\t\t\t{\n\t\t\t\t\"itemIdHost\": \"POS_001\",\n\t\t\t\t\"itemLabelHost\": \"My first position\",\n\t\t\t\t\"partners\": [\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"CONSIGNOR_STD\",\n\t\t\t\t\t\t\"name1\": \"Exporter AG\",\n\t\t\t\t\t\t\"countryIso\": \"DE\",\n\t\t\t\t\t\t\"companyReference\": \"N012345\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"SELLER_STD\",\n\t\t\t\t\t\t\"name1\": \"Seller AG\",\n\t\t\t\t\t\t\"countryIso\": \"DE\",\n\t\t\t\t\t\t\"companyReference\": \"N0654321\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"CONSIGNEE_STD\",\n\t\t\t\t\t\t\"name1\": \"Consignee AG\",\n\t\t\t\t\t\t\"countryIso\": \"IR\",\n\t\t\t\t\t\t\"companyReference\": \"N03333\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"BUYER_STD\",\n\t\t\t\t\t\t\"name1\": \"Buyer AG\",\n\t\t\t\t\t\t\"countryIso\": \"IR\",\n\t\t\t\t\t\t\"companyReference\": \"N04444\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"roleIdentCode\": \"ENDUSER_STD\",\n\t\t\t\t\t\t\"name1\": \"USER AG\",\n\t\t\t\t\t\t\"countryIso\": \"IR\",\n\t\t\t\t\t\t\"companyReference\": \"N02222\"\n\t\t\t\t\t}\n\t\t\t\t],\n\t\t\t\t\"decisiveDate\": \"2023-01-29T09:01:48.669Z\",\n\t\t\t\t\"productClassifications\": [\n\t\t\t\t\t{\n\t\t\t\t\t\t\"classificationIdentCode\": \"ClassificationAusfuhrliste\",\n\t\t\t\t\t\t\"classificationNumber\": \"1A001\"\n\t\t\t\t\t},\n\t\t\t\t\t{\n\t\t\t\t\t\t\"classificationIdentCode\": \"CLASSIFICATION_US_EAR_CCL\",\n\t\t\t\t\t\t\"classificationNumber\": \"1A001\"\n\t\t\t\t\t}\n\t\t\t\t],\n\t\t\t\t\"valueOfGoods\": [\n\t\t\t\t\t{\n\t\t\t\t\t\t\"value\": 100000,\n\t\t\t\t\t\t\"currencyIso\": \"EUR\"\n\t\t\t\t\t}\n\t\t\t\t],\n\t\t\t\t\"orderNumber\": \"ORDER_NO54321\",\n\t\t\t\t\"quantity\": 100,\n\t\t\t\t\"quantityUnit\": \"ST\"\n\t\t\t}\n\t\t]\n\t},\n\t\"profileIdentCode\": \"EC_RA_PROFILE\",\n\t\"isAutoCreateClearings\": false,\n\t\"riskAssessmentParms\": {\n\t\t\"templateId\": \"000002\",\n\t\t\"isRiskAssessmentRequested\": true,\n\t\t\"isDataForRAComplete\": true,\n\t\t\"questionnaireData\": {\n\t\t\t\"userName\": \"BEN003\",\n\t\t\t\"department\": \"Sales\",\n\t\t\t\"emailAddress\": \"user@mail.com\"\n\t\t}\n\t}\n}",
      "language": "json"
    },
    {
      "code": "<soapenv:Envelope xmlns:soapenv=\"http://schemas.xmlsoap.org/soap/envelope/\" xmlns:urn=\"urn:de.aeb.xnsg.expctrl.bf.v40\">\n\t<soapenv:Header/>\n\t<soapenv:Body>\n\t\t<urn:checkTransaction>\n\t\t\t<request>\n\t\t\t\t<clientSystemId>API-TEST</clientSystemId>\n\t\t\t\t<clientIdentCode>APITEST</clientIdentCode>\n\t\t\t\t<userName>BEN003</userName>\n\t\t\t\t<resultLanguageIsoCodes>en</resultLanguageIsoCodes>\n\t\t\t\t<transaction>\n\t\t\t\t\t<transactionIdHost>TRANS_002</transactionIdHost>\n\t\t\t\t\t<transactionLabelHost>My 2nd Order</transactionLabelHost>\n\t\t\t\t\t<items>\n\t\t\t\t\t\t<itemIdHost>POS_001</itemIdHost>\n\t\t\t\t\t\t<itemLabelHost>My first Position</itemLabelHost>\n\t\t\t\t\t\t<partners>\n\t\t\t\t\t\t\t<roleIdentCode>CONSIGNOR_STD</roleIdentCode>\n\t\t\t\t\t\t\t<name1>Exporter AG</name1>\n\t\t\t\t\t\t\t<countryIso>DE</countryIso>\n\t\t\t\t\t\t\t<companyReference>N012345</companyReference>\n\t\t\t\t\t\t</partners>\n\t\t\t\t\t\t<partners>\n\t\t\t\t\t\t\t<roleIdentCode>SELLER_STD</roleIdentCode>\n\t\t\t\t\t\t\t<name1>Seller AG</name1>\n\t\t\t\t\t\t\t<countryIso>DE</countryIso>\n\t\t\t\t\t\t\t<companyReference>N0654321</companyReference>\n\t\t\t\t\t\t</partners>\n\t\t\t\t\t\t<partners>\n\t\t\t\t\t\t\t<roleIdentCode>CONSIGNEE_STD</roleIdentCode>\n\t\t\t\t\t\t\t<name1>Consignee AG</name1>\n\t\t\t\t\t\t\t<countryIso>IR</countryIso>\n\t\t\t\t\t\t\t<companyReference>N03333</companyReference>\n\t\t\t\t\t\t</partners>\n\t\t\t\t\t\t<partners>\n\t\t\t\t\t\t\t<roleIdentCode>BUYER_STD</roleIdentCode>\n\t\t\t\t\t\t\t<name1>Buyer AG</name1>\n\t\t\t\t\t\t\t<countryIso>IR</countryIso>\n\t\t\t\t\t\t\t<companyReference>N04444</companyReference>\n\t\t\t\t\t\t</partners>\n\t\t\t\t\t\t<partners>\n\t\t\t\t\t\t\t<roleIdentCode>ENDUSER_STD</roleIdentCode>\n\t\t\t\t\t\t\t<name1>USER AG</name1>\n\t\t\t\t\t\t\t<countryIso>IR</countryIso>\n\t\t\t\t\t\t\t<companyReference>N02222</companyReference>\n\t\t\t\t\t\t</partners>\n\t\t\t\t\t\t<decisiveDate>2023-01-18T00:00:00+02:00</decisiveDate>\n\t\t\t\t\t\t<productClassifications>\n\t\t\t\t\t\t\t<classificationIdentCode>ClassificationAusfuhrliste</classificationIdentCode>\n\t\t\t\t\t\t\t<classificationNumber>1A001</classificationNumber>\n\t\t\t\t\t\t</productClassifications>\n\t\t\t\t\t\t<productClassifications>\n\t\t\t\t\t\t\t<classificationIdentCode>CLASSIFICATION_US_EAR_CCL</classificationIdentCode>\n\t\t\t\t\t\t\t<classificationNumber>1A001</classificationNumber>\n\t\t\t\t\t\t</productClassifications>\n\t\t\t\t\t\t<valueOfGoods>\n\t\t\t\t\t\t\t<value>100000</value>\n\t\t\t\t\t\t\t<currencyIso>EUR</currencyIso>\n\t\t\t\t\t\t</valueOfGoods>\n\t\t\t\t\t\t<orderNumber>ORDER_NO54321</orderNumber>\n\t\t\t\t\t\t<quantity>100</quantity>\n\t\t\t\t\t\t<quantityUnit>ST</quantityUnit>\n\t\t\t\t\t</items>\n\t\t\t\t</transaction>\n\t\t\t\t<profileIdentCode>EC_RA_PROFILE</profileIdentCode>\n\t\t\t\t<isAutoCreateClearings>false</isAutoCreateClearings>\n\t\t\t\t<riskAssessmentParms>\n\t\t\t\t\t<templateId>000002</templateId>\n\t\t\t\t\t<isRiskAssessmentRequested>true</isRiskAssessmentRequested>\n\t\t\t\t\t<isDataForRAComplete>true</isDataForRAComplete>\n\t\t\t\t\t<questionnaireData>\n\t\t\t\t\t\t<userName>BEN003</userName>\n\t\t\t\t\t\t<department>Sales</department>\n\t\t\t\t\t\t<emailAddress>user@mail.com</emailAddress>\n\t\t\t\t\t</questionnaireData>\n\t\t\t\t</riskAssessmentParms>\n\t\t\t</request>\n\t\t</urn:checkTransaction>\n\t</soapenv:Body>\n</soapenv:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]

[block:api-header]
{
  "title": "Response"
}
[/block]
The response contains the information whether an export is allowed, something has to be done still, or the export is prohibited. See also [Results](doc:results).
[block:code]
{
  "codes": [
    {
      "code": "{\n  \"hasErrors\": false,\n  \"hasOnlyRetryableErrors\": false,\n  \"hasWarnings\": false,\n  \"messages\": [],\n  \"totalResultType\": \"RESTRICTION\",\n  \"itemResults\": [\n    {\n      \"itemIdHost\": \"POS_001\",\n      \"resultType\": \"RESTRICTION\",\n      \"pluginResults\": [\n        {\n          \"pluginIdentCode\": \"DE-EU-Plugin\",\n          \"resultType\": \"RESTRICTION\",\n          \"approvals\": []\n        },\n        {\n          \"pluginIdentCode\": \"US-EAR-Plugin\",\n          \"resultType\": \"RESTRICTION\",\n          \"approvals\": []\n        },\n        {\n          \"pluginIdentCode\": \"Risk-Assessment-Plugin\",\n          \"resultType\": \"CHECK\",\n          \"approvals\": []\n        }\n      ]\n    }\n  ]\n}",
      "language": "json"
    },
    {
      "code": "<S:Envelope xmlns:S=\"http://schemas.xmlsoap.org/soap/envelope/\">\n\t<S:Body>\n\t\t<ns2:checkTransactionResponse xmlns:ns2=\"urn:de.aeb.xnsg.expctrl.bf.v40\">\n\t\t\t<result>\n\t\t\t\t<hasErrors>false</hasErrors>\n\t\t\t\t<hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>\n\t\t\t\t<hasWarnings>false</hasWarnings>\n\t\t\t\t<totalResultType>RESTRICTION</totalResultType>\n\t\t\t\t<itemResults>\n\t\t\t\t\t<itemIdHost>POS_001</itemIdHost>\n\t\t\t\t\t<resultType>RESTRICTION</resultType>\n\t\t\t\t\t<pluginResults>\n\t\t\t\t\t\t<pluginIdentCode>DE-EU-Plugin</pluginIdentCode>\n\t\t\t\t\t\t<resultType>RESTRICTION</resultType>\n\t\t\t\t\t</pluginResults>\n\t\t\t\t\t<pluginResults>\n\t\t\t\t\t\t<pluginIdentCode>US-EAR-Plugin</pluginIdentCode>\n\t\t\t\t\t\t<resultType>RESTRICTION</resultType>\n\t\t\t\t\t</pluginResults>\n\t\t\t\t\t<pluginResults>\n\t\t\t\t\t\t<pluginIdentCode>Risk-Assessment-Plugin</pluginIdentCode>\n\t\t\t\t\t\t<resultType>RESTRICTION</resultType>\n\t\t\t\t\t</pluginResults>\n\t\t\t\t</itemResults>\n\t\t\t</result>\n\t\t</ns2:checkTransactionResponse>\n\t</S:Body>\n</S:Envelope>",
      "language": "xml",
      "name": "XML (SOAP)"
    }
  ]
}
[/block]