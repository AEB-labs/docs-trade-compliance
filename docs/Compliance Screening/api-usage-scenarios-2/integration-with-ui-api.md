---
title: Screening Integration with UI-API
deprecated: false
hidden: false
metadata:
  robots: index
---
In this scenario, the partner system integration will be tighter than with synchronization for changes in Compliance Screening _match handling_ alone. Therefore, the effort to implement it will be higher.

See [Integration with API-synchronization for match handling](https://trade-compliance.docs.developers.aeb.com/docs/screening-integration-with-synchronization) for an introduction to screening with synchronization.

Please note that for technical reasons the singleMatchHandlingStatus-API can only be used in partner systems which also use the synchronization API. We also advise against re-checks of addresses to derive their match handling status from the response in this case.
The UI API however, can be used as a stand-alone entry point to the AEB Compliance Screening GUI as well.

### Step 1

In this scenario, a user starts by providing all relevant information to their partner system and triggers an API call to AEBs Compliance Screening (either using the screenAddresses [REST](ref:screenaddresses) or the batchMatch [SOAP](https://rz3.aeb.de/test4ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#batchMatch-de.aeb.xnsg.rex.bf.AddressPatternDTO:A-de.aeb.xnsg.rex.bf.MatchParametersDTO-) API function).

Important: The clientReferenceId field for each address to be checked should be filled with a unique reference. This reference can later be used to map the match handling results to the corresponding records in your partner system. Please note that screened addresses with an empty clientReferenceId field cannot be synchronized.

This will trigger AEBs address screening algorithm and check all supplied addresses. The partner system will receive a response with the information which addresses resulted in potential matches, which in turn should block any associated transaction or business partner and further processing of such transactions. We recommend creating a dedicated field for the blocked/released status in business partners in your partner system. If you wish, you may also configure email notifications whenever a match has been found.

### Step 2

The user will then evaluate all address matches in AEBs Compliance Screening. This is usually done through AEBs Compliance Screening GUI. For address matches that are found to be false positives, “Good Guys” can be created.

The Compliance Screening GUI can be accessed via the link in the response of a matchHandlingViewEntry API call (either using [REST](ref:matchHandlingViewEntry) or [SOAP](https://rz3.aeb.de/test5ce/servlet/bf/doc/RexAF/de/aeb/xnsg/rex/af/IRexAF.html#matchHandlingEntry\(de.aeb.xnsg.foundation.af.ApplicationFacadeParmsDTO,de.aeb.xnsg.rex.af.MatchHandlingEntryAFParmsDTO\))).

### Step 3

During the match handling in AEBs Compliance Screening GUI the synchronization events for match handling are automatically created and can periodically be requested by a partner system.
In addition, a partner system can request the match handling status of a single match via the singleMatchHandlingStatus API (either using [REST](ref:singleMatchHandlingStatus) or [SOAP](https://rz3.aeb.de/test5ce/servlet/bf/doc/RexBF/de/aeb/xnsg/rex/bf/IRexBF.html#getSingleMatchHandlingStatus\(de.aeb.xnsg.rex.bf.restdto.GetSingleMatchHandlingStatusRequestDTO\))) and thus does not have to wait for the next synchronization update to display the current match handling status.
Requests made via the singleMatchHandlingStatus API function do not influence following calls to the [synchronization API](https://trade-compliance.docs.developers.aeb.com/docs/screening-integration-with-synchronization) for match handling.
