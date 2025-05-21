---
title: Simple integrated screening
deprecated: false
hidden: false
metadata:
  robots: index
---
Let's start with a simple use case for running compliance screenings, in which a partner system calls AEBs Compliance Screening API once and the result is typically evaluated and acted upon by a *Compliance Officer*.

<Image align="center" width="123% " src="https://files.readme.io/f7241cfa2650ddac7da0bd16b706738c777d8a1573c4ab4319868f55c7a908f3-Slide1.JPG" />

![](https://files.readme.io/1aa447fbe2d22dba8245ac7312914486591f8bfc63cd53c63e17c9e0575da5f5-image.png)

### Step 1

In this scenario, a user starts by providing all relevant information to their partner system. Once finalised, the user can trigger an API call to AEB Compliance Screening (either using the screenAddresses ([REST](https://trade-compliance.docs.developers.aeb.com/v4.1/update/reference#/)) or the batchMatch (SOAP) endpoint). This will trigger AEB´s address screening algorithm and check all supplied addresses against licensed restricted party lists. The results of this screening are logged automatically. The response back to the partner system will show whether a potential address match has been found or not. Most users will also configure an automatic e-mail notification, should an address match arise.

### Step 2

The user will then evaluate all address matches in AEB Compliance Screening. For address matches that are found to be false positives, a “Good Guy” can be created, which can be the case for a user's business partners, that have similar names to restricted parties. For actual address matches, the user will have to proceed according to their internally defined actions for dealing with restricted parties.