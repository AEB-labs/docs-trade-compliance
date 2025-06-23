---
title: Screening with integrated good guy definition
deprecated: false
hidden: false
metadata:
  robots: index
---
Lastly, in this less common use case, all steps of the screening process and the subsequent handling of any potential matches are fully integrated into a partner system. This requires multiple API calls to different endpoints.

<Image align="center" src="https://files.readme.io/632a4f59045d437b14db7ec84f609754fd8b543867f7b990a8f1424584e99a88-Szenario5.png" />

### Step 1

In this scenario, a user starts by providing all relevant information to their partner system. Once finalised, the user can trigger an API call to AEB Compliance Screening (either using the screenAddresses ([REST](https://trade-compliance.docs.developers.aeb.com/v4.1/update/reference/screenaddresses#/)) or the batchMatch ([SOAP](https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#batchMatch-de.aeb.xnsg.rex.bf.AddressPatternDTO:A-de.aeb.xnsg.rex.bf.MatchParametersDTO-)) endpoint). This will trigger the address screening algorithm and check all supplied addresses against licensed restricted party lists with the results being logged automatically. The partner system will show whether a potential address match has been found or not.

### Step 2

For a detailed evaluation of any potential address match, the user then triggers a call to the findMatchingAddresses ([REST](https://trade-compliance.docs.developers.aeb.com/v4.1/update/reference/findmatchingaddresses#/)) or getMatchingAddresses ([SOAP](https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getMatchingAddresses\(de.aeb.xnsg.rex.bf.AddressPatternDTO,de.aeb.xnsg.rex.bf.MatchParametersDTO\))) endpoint. The responses of these endpoints contains more detailed information on every individual address and should only be called on addresses that have been found to be potential matches via screenAddresses/batchMatch.

### Step 3

After the user has evaluated all relevant information, they can either define “Good Guys” for false positive address matches or take internally defined actions on restricted business partners. “Good Guys” can be defined through API calls using either the goodGuy ([REST](https://trade-compliance.docs.developers.aeb.com/v4.1/update/reference/goodguy-1#/)) or the defineGoodGuyWithResult ([SOAP](https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#defineGoodGuyWithResult\(de.aeb.xnsg.rex.bf.GoodGuyAddressDTO\))) endpoint, which will create “Good Guys” and log their creation.

### Step 4

Once any potential match has been handled accordingly, the partner system triggers another API call to re-screen any blocked address, which returns with no further address matches found and therefore blocked transactions are released and may proceed.