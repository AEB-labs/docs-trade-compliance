---
title: Simple integrated screening
deprecated: false
hidden: false
metadata:
  robots: index
---
Let's start with a simple use case for running compliance screenings, in which a partner system calls AEB's Compliance Screening API once and the result is typically evaluated and acted upon by a *Compliance Officer* through the AEB Compliance Screening GUI.

<Image align="center" width="123% " src="https://files.readme.io/f7241cfa2650ddac7da0bd16b706738c777d8a1573c4ab4319868f55c7a908f3-Slide1.JPG" />

### Step 1

In this scenario, a user starts by providing all relevant information to their partner system. 
Once finalised, the user can trigger an API call to AEB's Compliance Screening (either using the screenAddresses ([REST](ref:screenaddresses)) or the batchMatch ([SOAP](https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#batchMatch-de.aeb.xnsg.rex.bf.AddressPatternDTO:A-de.aeb.xnsg.rex.bf.MatchParametersDTO-) API function). 
This will trigger AEB´s address screening algorithm and check all supplied addresses against restricted party lists. The results of this screening are logged automatically. The response back to the partner system will show whether a potential address match has been found or not. Most users will also configure an automatic e-mail notification, should an address match arise.

### Step 2

The user will then evaluate all address matches in AEB's Compliance Screening GUI. For address matches that are found to be false positives, a “Good Guy” can be created, which often is the case for a user's business partners, that have similar names to restricted parties. For actual address matches, the user will have to proceed according to their internally defined actions for dealing with restricted parties.