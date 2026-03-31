---
title: Integration with API-synchronization for match handling
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
In this scenario, the partner system integration will be tighter and more automated. Therefore, the effort to implement it will be higher.

To enable the synchronization for changes in Compliance Screening *match handling*, a partner system should subscribe to synchronization events of Compliance Screening *MatchHandlingSyncDigest*. This could be done directly in the Compliance Screening web application (*Office – Administration – Synchronization – Partner system subscriptions*) or via the [synchronization API](doc:sync-bf-calls-overview).

![1286](https://files.readme.io/c88a30b-csWithSync.png "csWithSync.png")

### Step 1

In this scenario, a user starts by providing all relevant information to their partner system and triggers an API call to AEB Compliance Screening (either using the screenAddresses [REST](ref:screenaddresses) or the batchMatch [SOAP](https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#batchMatch-de.aeb.xnsg.rex.bf.AddressPatternDTO:A-de.aeb.xnsg.rex.bf.MatchParametersDTO-) API function. 
This will trigger AEBs address screening algorithm and check all supplied addresses. The partner system will receive a response with the information which addresses resulted in potential matches, which in turn should block any associated transaction or business partner and further processing of such transactions. We recommend creating a dedicated field for the blocked/released status in business partners in your partner system.
If you wish, you may also configure email notifications whenever a match has been found.

### Step 2

The user will then evaluate all address matches in AEB Compliance Screening. 
This is usually done through AEBs Compliance Screening GUI. 
For address matches that are found to be false positives, “Good Guys” can be created.

 Once an address matches has been handled, a synchronization event (*journal entry*) is generated and stored in Trade Compliance Management. The synchronization events are created only if the partner system has subscribed to synchronization events for match handling and contain information about the changed match handling results.

A batch job on the partner system should periodically call [getMatchHandlingChanges()](ref:getmatchhandlingchanges) to get the new results of the match handling. The addresses in the partner system corresponding to the changed match handling results can be re-checked (if a good guy was created) or remain blocked.

After the changed match handling results are processed and the corresponding matches are updated, the partner system should call [acknowledgeGetMatchHandlingChanges()](ref:acknowledgegetmatchhandlingchanges) to mark the synchronization events, identified by the syncId returned in the response from [getMatchHandlingChanges()](ref:getmatchhandlingchanges), as processed.

> 📘 To get more information about the synchronization API and about what changes in Compliance Screening match handling trigger the synchronization events see [About Synchronization API](doc:about-synchronization-api).
