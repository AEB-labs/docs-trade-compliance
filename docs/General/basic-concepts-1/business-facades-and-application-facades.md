---
title: Types of API Functions
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
The Trade Compliance Management APIs provide two types of API functions:

* *Business APIs* that allow the use of Trade Compliance Management functionality in your own program code.
* *UI APIs* that offer the possibility to embed the Trade Compliance Management GUI in your own software. 

> 📘 A UI API call is technically a standard API call - the authentication process is the same and request parameters are transmitted as HTTP body.\
> But a UI API returns a link in the response, which the caller can open in a new browser window or in an embedded frame of the web application, allowing the user to access the desired Trade Compliance Management application. 

> 🚧 In the past, the terms *Business Facade* (BF) and *Application Facade* (AF) were used for these two types of APIs. 
> The term *Business Facade* is now replaced by *Business API*, and the term *Application Facade* is replaced by *UI API*. The old terms may still be used in some places for technical reasons, e.g. in class names of the SOAP API variant.