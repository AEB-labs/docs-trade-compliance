---
title: Setting up Your Environment
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
## Credentials

Before you can start using the API, you need a client, user and password.

If you do not have your own client yet, you can use the following credentials to test the API:

Client: APITEST\
User: API\_TEST\
PW: API\_TEST\_007

The API is available via [REST](ref:) or <a href="https://rz3.aeb.de/test4ce/servlet/bf?lang=en" target="_blank">SOAP</a> webservices.

> ❗️
>
> The client <strong>APITEST</strong> is intended for basic connectivity testing and is used by different users. Don't use it with sensitive data.

### Customer-specific credentials

In case you have a dedicated client for your TCM solution, you should use a client-specific API-user that should either be created by AEB or by your TCM administrator.

> 🚧
>
> Please make sure, that the API-user has the role  **I\_BUSINESSFACADE** and that the option "Dialog user" is not checked.

## Base URL

To access the REST or SOAP webservices, you will need a base URL as an entry point to the AEB Compliance Screening API. Your company will be assigned a base URL when signing a contract with AEB. For our API test environment, the base URL is as follows:

| Technology | Base URL                                                                               |
| :--------- | :------------------------------------------------------------------------------------- |
| REST       | [https://rz3.aeb.de/test4ce/rest](https://rz3.aeb.de/test4ce/rest)                     |
| SOAP       | [https://rz3.aeb.de:443/test4ce/servlet/bf](https://rz3.aeb.de:443/test4ce/servlet/bf) |

> 📘
>
> The API is only available via HTTPS.

## Authentication

Depending on the technology (REST or SOAP) different authentication methods could be used:

* **HTTP Basic Authentication**: This can be used with REST and SOAP and requires authentication data to be provided with each call.
* **Token Authentication**: This can only be used with REST and requires an additional call to request a token, that can then be used for subsequent calls for a limited time.

### HTTP Basic Authentication

With this method, authentication data must be provided for every API call. It works for REST and SOAP.\
It is expected as HTTP authentication (HTTP Basic Authentication according to RFC 2617).

The user and client login data is transmitted in the format <strong>user@client:password</strong>. The login data must be base 64–encoded.  Before the conversion, the login data should use ISO-8859-1 character coding. If no umlauts or other diacritics are included, this corresponds to ASCII coding. It is also possible to use Windows character coding (CP-1252) if no euro sign is included. 

Base 64 encoding is no encryption in cryptographic terms, but still plain text. This is why we require using HTTPS encryption so the data cannot be intercepted by unauthorized parties.

Example for the coding of login data:\
User = API\_TEST\
Client = APITEST\
Password = API\_TEST\_007

The string "API\_TEST\@APITEST:API\_TEST\_007", when encoded in base 64, yields “QVBJX1RFU1RAQVBJVEVTVDpBUElfVEVTVF8wMDc=". The following line would therefore be added to the HTTP header:

<strong>Authorization: Basic QVBJX1RFU1RAQVBJVEVTVDpBUElfVEVTVF8wMDc=</strong>

> 📘
>
> Note that the client and user specified here are used only for authentication and have no impact on the business logic.

> 🚧
>
> If you are using "Try it!" via [REST](ref:),  remember to use\ <strong> user\@client</strong> as username in the "AUTHORIZATION" field and switch to "Basic"

> 🚧
>
> To test REST APIs manually, you can also use this <a href="https://rz3.aeb.de/test4ce/swagger/#/" target="_blank">link</a> to our REST API swagger documentation and click the <strong>"Try it out"</strong> button for the desired request. Do not forget to use the <strong>“Authorize”</strong> button for authentication (at the top of the web page). Otherwise, you will get a 403 HTTP error.

### Token Authentication

This method works for REST **only**. First you have to request an authentication token by using the URL [https://rz3.aeb.de/test4ce/rest/logon/user](https://rz3.aeb.de/test4ce/rest/logon/user):

```Text JSON
{
	"clientName": "APITEST",
	"userName": "API_TEST",
	"password": "API_TEST_007",
	"localeName": "en",
	"isExternalLogon": "true"
}
```

You will then get a token back, which you have to use as request header in subsequent requests\
(the header is ***X-XNSG\_WEB\_TOKEN***).

The token is valid for a maximum of twelve hours and can be reused for several calls. A good approach is to request a new token every hour or/and if an authentication error is given (e.g. token is expired or not valid anymore after application restart).

Each following request should then contain the retrieved token in the request header:

```
POST /test4ce/rest/ComplianceFoundation/getMasterdataIdentifiers HTTP/1.1
Host: rz3.aeb.de
Connection: keep-alive
accept: application/json
...
X-XNSG_WEB_TOKEN: eyJlbmdpbmVJZCI6IjUwMzE2OTEwNF9XbVZ3VGV4YWVGIiwiaWQiOiJVU0VSX0NMSUVOVCJ9.eyJ1c2VyTmFtZSI6IldTTSIsImNsaWVudElkZW50Q29kZSI6IlVOSVRFREIifQ==.AwgakGOMN0IRJo6cGkVS1DXpbGOozG7o8vQD3DEalYb2oE0qRUmifyh9vfms1NWeMwTJUpelRo9fLy5eSm92k+vull2q3GJfhkVT7Oqa9HUobIZFSDVPL4z5++ovnemuyuz2qZdTXHP6qPepk+DV2WTitam0zgNGAJidGBUK/Q4=
...

```