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

## Check transaction

You can use the following example and copy/paste it into your favorite tool to test REST and/or SOAP API calls. Our test environment is prepared to work with the data in this example.

> 📘 To reuse this example for your login details, replace the field clientIdentCode with your client, the field profileIdentCode with your Compliance profile and the field clientSystemId with an ID for your calling system.

When using REST, the URL for the request in our API test environment will be\
[https://rz3.aeb.de/test4ce/rest/ExportControl/v2/checkTransaction](https://rz3.aeb.de/test4ce/rest/ExportControl/v2/checkTransaction).\
When using SOAP, the URL for the request in our API test environment will be\ <a href="https://rz3.aeb.de:443/test4ce/servlet/bf/ExportControl40V2BF?WSDL">https\://rz3.aeb.de:443/test4ce/servlet/bf/ExportControl40V2BF</a>.

> 📘 To test REST API manually you can use this <a href="https://rz3.aeb.de/test4ce/swagger/#/" target="_blank">link</a> to our REST API documentation and click the "Try it out" button for the desired request. Do not forget to use the “Authorize” button for authentication (at the top of the web page). Otherwise, you will get a 403 HTTP error.

```json
{
	"clientSystemId": "API-TEST",
	"clientIdentCode": "APITEST",
	"userName": "BEN003",
	"resultLanguageIsoCodes": [
		"en"
	],
	"transaction": {
		"transactionIdHost": "TRANS_002",
		"transactionLabelHost": "My 2nd Order",
		"items": [
			{
				"itemIdHost": "POS_001",
				"itemLabelHost": "My first position",
				"partners": [
					{
						"roleIdentCode": "CONSIGNOR_STD",
						"name1": "Exporter AG",
						"countryIso": "DE",
						"companyReference": "N012345"
					},
					{
						"roleIdentCode": "SELLER_STD",
						"name1": "Seller AG",
						"countryIso": "DE",
						"companyReference": "N0654321"
					},
					{
						"roleIdentCode": "CONSIGNEE_STD",
						"name1": "Consignee AG",
						"countryIso": "IR",
						"companyReference": "N03333"
					},
					{
						"roleIdentCode": "BUYER_STD",
						"name1": "Buyer AG",
						"countryIso": "IR",
						"companyReference": "N04444"
					},
					{
						"roleIdentCode": "ENDUSER_STD",
						"name1": "USER AG",
						"countryIso": "IR",
						"companyReference": "N02222"
					}
				],
				"decisiveDate": "2023-01-29T09:01:48.669Z",
				"productClassifications": [
					{
						"classificationIdentCode": "ClassificationAusfuhrliste",
						"classificationNumber": "1A001"
					},
					{
						"classificationIdentCode": "CLASSIFICATION_US_EAR_CCL",
						"classificationNumber": "1A001"
					}
				],
				"valueOfGoods": [
					{
						"value": 100000,
						"currencyIso": "EUR"
					}
				],
				"orderNumber": "ORDER_NO54321",
				"quantity": 100,
				"quantityUnit": "ST"
			}
		]
	},
	"profileIdentCode": "EC_RA_PROFILE",
	"isAutoCreateClearings": false,
	"riskAssessmentParms": {
		"templateId": "000002",
		"isRiskAssessmentRequested": true,
		"isDataForRAComplete": true,
		"questionnaireData": {
			"userName": "BEN003",
			"department": "Sales",
			"emailAddress": "user@mail.com"
		}
	}
}
```
```xml XML (SOAP)
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:de.aeb.xnsg.expctrl.bf.v40">
	<soapenv:Header/>
	<soapenv:Body>
		<urn:checkTransaction>
			<request>
				<clientSystemId>API-TEST</clientSystemId>
				<clientIdentCode>APITEST</clientIdentCode>
				<userName>BEN003</userName>
				<resultLanguageIsoCodes>en</resultLanguageIsoCodes>
				<transaction>
					<transactionIdHost>TRANS_002</transactionIdHost>
					<transactionLabelHost>My 2nd Order</transactionLabelHost>
					<items>
						<itemIdHost>POS_001</itemIdHost>
						<itemLabelHost>My first Position</itemLabelHost>
						<partners>
							<roleIdentCode>CONSIGNOR_STD</roleIdentCode>
							<name1>Exporter AG</name1>
							<countryIso>DE</countryIso>
							<companyReference>N012345</companyReference>
						</partners>
						<partners>
							<roleIdentCode>SELLER_STD</roleIdentCode>
							<name1>Seller AG</name1>
							<countryIso>DE</countryIso>
							<companyReference>N0654321</companyReference>
						</partners>
						<partners>
							<roleIdentCode>CONSIGNEE_STD</roleIdentCode>
							<name1>Consignee AG</name1>
							<countryIso>IR</countryIso>
							<companyReference>N03333</companyReference>
						</partners>
						<partners>
							<roleIdentCode>BUYER_STD</roleIdentCode>
							<name1>Buyer AG</name1>
							<countryIso>IR</countryIso>
							<companyReference>N04444</companyReference>
						</partners>
						<partners>
							<roleIdentCode>ENDUSER_STD</roleIdentCode>
							<name1>USER AG</name1>
							<countryIso>IR</countryIso>
							<companyReference>N02222</companyReference>
						</partners>
						<decisiveDate>2023-01-18T00:00:00+02:00</decisiveDate>
						<productClassifications>
							<classificationIdentCode>ClassificationAusfuhrliste</classificationIdentCode>
							<classificationNumber>1A001</classificationNumber>
						</productClassifications>
						<productClassifications>
							<classificationIdentCode>CLASSIFICATION_US_EAR_CCL</classificationIdentCode>
							<classificationNumber>1A001</classificationNumber>
						</productClassifications>
						<valueOfGoods>
							<value>100000</value>
							<currencyIso>EUR</currencyIso>
						</valueOfGoods>
						<orderNumber>ORDER_NO54321</orderNumber>
						<quantity>100</quantity>
						<quantityUnit>ST</quantityUnit>
					</items>
				</transaction>
				<profileIdentCode>EC_RA_PROFILE</profileIdentCode>
				<isAutoCreateClearings>false</isAutoCreateClearings>
				<riskAssessmentParms>
					<templateId>000002</templateId>
					<isRiskAssessmentRequested>true</isRiskAssessmentRequested>
					<isDataForRAComplete>true</isDataForRAComplete>
					<questionnaireData>
						<userName>BEN003</userName>
						<department>Sales</department>
						<emailAddress>user@mail.com</emailAddress>
					</questionnaireData>
				</riskAssessmentParms>
			</request>
		</urn:checkTransaction>
	</soapenv:Body>
</soapenv:Envelope>
```

## Response

The response contains the information whether an export is allowed, something has to be done still, or the export is prohibited. See also [Results](doc:results).

```json
{
  "hasErrors": false,
  "hasOnlyRetryableErrors": false,
  "hasWarnings": false,
  "messages": [],
  "totalResultType": "RESTRICTION",
  "itemResults": [
    {
      "itemIdHost": "POS_001",
      "resultType": "RESTRICTION",
      "pluginResults": [
        {
          "pluginIdentCode": "DE-EU-Plugin",
          "resultType": "RESTRICTION",
          "approvals": []
        },
        {
          "pluginIdentCode": "US-EAR-Plugin",
          "resultType": "RESTRICTION",
          "approvals": []
        },
        {
          "pluginIdentCode": "Risk-Assessment-Plugin",
          "resultType": "CHECK",
          "approvals": []
        }
      ]
    }
  ]
}
```
```xml XML (SOAP)
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/">
	<S:Body>
		<ns2:checkTransactionResponse xmlns:ns2="urn:de.aeb.xnsg.expctrl.bf.v40">
			<result>
				<hasErrors>false</hasErrors>
				<hasOnlyRetryableErrors>false</hasOnlyRetryableErrors>
				<hasWarnings>false</hasWarnings>
				<totalResultType>RESTRICTION</totalResultType>
				<itemResults>
					<itemIdHost>POS_001</itemIdHost>
					<resultType>RESTRICTION</resultType>
					<pluginResults>
						<pluginIdentCode>DE-EU-Plugin</pluginIdentCode>
						<resultType>RESTRICTION</resultType>
					</pluginResults>
					<pluginResults>
						<pluginIdentCode>US-EAR-Plugin</pluginIdentCode>
						<resultType>RESTRICTION</resultType>
					</pluginResults>
					<pluginResults>
						<pluginIdentCode>Risk-Assessment-Plugin</pluginIdentCode>
						<resultType>RESTRICTION</resultType>
					</pluginResults>
				</itemResults>
			</result>
		</ns2:checkTransactionResponse>
	</S:Body>
</S:Envelope>
```
