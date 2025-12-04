---
title: Screening with integrated status synchronization
deprecated: false
hidden: false
metadata:
  robots: index
---
Next up is the most common integration, which consists of two individual calls to AEBs Compliance Screening API. The results from the initial screening call is typically evaluated and acted upon by a _Compliance Officer_. You can find more details on what the status syncronization is [here](https://trade-compliance.docs.developers.aeb.com/v4.1/update/docs/status-syncronization#/).

<Image align="center" border={false} src="https://files.readme.io/e7e8876e42b5a216a3a4421e07265ec78445c3c6b29f7fcde974ad44622f106b-Slide4.JPG" />

### Step 1

In this scenario, a user starts by providing all relevant information to their partner system and triggers an API call to AEB Compliance Screening (either using the screenAddresses [REST](ref:screenaddresses) or the batchMatch [SOAP](https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#batchMatch-de.aeb.xnsg.rex.bf.AddressPatternDTO:A-de.aeb.xnsg.rex.bf.MatchParametersDTO-) API function. 
This will trigger AEBs address screening algorithm and check all supplied addresses. The partner system will receive a response with the information which addresses resulted in potential matches, which in turn should block any associated transaction or business partner and further processing of such transactions. We recommend creating a dedicated field for the blocked/released status in business partners in your partner system.
If you wish, you may also configure email notifications whenever a match has been found.

### Step 2

The user will then evaluate all address matches in AEB Compliance Screening. 
This is usually done through AEBs Compliance Screening GUI. 
For address matches that are found to be false positives, “Good Guys” can be created.

### Step 3

Once all address matches are handled, the partner system should run a status syncronization by calling screenAddresses or batchMatch again. This will update all statuses for business partners and listed entities should be blocked in your partner system.

Should your evaluation results in a positive match, i.e., an entity on a restricted party list, we recommend you separate those from your automated screening calls and add them to a dedicated list, which you can screen individually.
