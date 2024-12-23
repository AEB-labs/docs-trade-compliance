---
title: Embedding the AEB GUI into Your Software
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
##General information about Compliance Screening applications
Besides business facades (BF), which allow the use of Compliance Screening functionality in your own program code, the AEB Compliance Screening API also offers application facades (AF) to embed the GUI of Compliance Screening in your own software.
[block:parameters]
{
  "data": {
    "0-0": "REST",
    "0-1": "[Compliance Screening Applications](ref:compliance-screening-applications-1)",
    "1-0": "SOAP",
    "1-1": "<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/RexAF?WSDL\" target=\"_blank\">RexAF (WSDL)</a>\n<a href=\"https://rz3.aeb.de/test4ce/servlet/bf/doc/RexAF/de/aeb/xnsg/rex/af/IRexAF.html\" target=\"_blank\">RexAF (JavaDoc)</a>",
    "h-1": "Link to documentation",
    "h-0": "Technology"
  },
  "cols": 2,
  "rows": 2
}
[/block]
An application facade call is technically a normal business facade call - the authentication process is the same, request parameters are transmitted as HTTP body. But an application facade returns a link in the response, which the caller of the application facade can open in a new browser window or in an embedded frame of the web application, so the desired application of Compliance Screening opens for the user.

More details on application facade requests can be found in [REST](ref:compliance-screening-applications-1) or <a href="https://rz3.aeb.de/test4ce/servlet/bf?lang=en" target="_blank">SOAP</a> documentation.