---
title: Business Facades and Application Facades
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
The Trade Compliance Management APIs support two types of API calls:
+ business facades (BF):  BFs allow the use of Trade Compliance Management functionality in your own program code.
+ application facades (AF): AFs offer the possibility to embed the Trade Compliance Management GUI in your own software. 

[block:callout]
{
  "type": "info",
  "body": "An application facade call is technically a normal business facade call - the authentication process is the same and request parameters are transmitted as HTTP body. \nBut an application facade returns a link in the response, which the caller of the application facade can open in a new browser window or in an embedded frame of the web application, so the desired application of Trade Compliance Management opens for the user."
}
[/block]