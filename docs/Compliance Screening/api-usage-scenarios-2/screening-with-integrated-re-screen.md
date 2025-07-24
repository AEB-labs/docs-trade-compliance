---
title: Screening with integrated status synchronization
deprecated: false
hidden: false
metadata:
  robots: index
---
Next up is the most common integration, which consists of two individual calls to AEBs Compliance Screening API. The results from the initial screening call is typically evaluated and acted upon by a *Compliance Officer*.

<Image align="center" src="https://files.readme.io/54f4d7fc5b1449c7e035c4463a85c97895d021dc3e4dea0dc704f28fa2fca6f3-Scenario_2.png" />

### Step 1

In this scenario, a user starts by providing all relevant information to their partner system and triggers an API call to AEB Compliance Screening (either using the screenAddresses [REST](https://trade-compliance.docs.developers.aeb.com/v4.1/update/reference/screenaddresses#/)  or the batchMatch [SOAP](https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#batchMatch-de.aeb.xnsg.rex.bf.AddressPatternDTO:A-de.aeb.xnsg.rex.bf.MatchParametersDTO-) endpoint . This will trigger AEBs address screening algorithm and check all supplied addresses. The partner system will receive a response with the information which addresses resulted in potential matches, which in turn should block any associated transaction or business partner and further processing of such transactions.

### Step 2

The user will then evaluate all address matches in AEB Compliance Screening. This is usually done through AEBs Compliance Screening GUI. For address matches that are found to be false positives, “Good Guys” can be created.

### Step 3

Once all address matches are handled, a re-screen can be triggered, either by a user directly or through an automated configuration in the partner system and the response with no further address matches found releases previously blocked transactions.