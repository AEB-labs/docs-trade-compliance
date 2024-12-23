---
title: API Usage Scenarios
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
[block:api-header]
{
  "title": "Risk Assessment integration into Export Control checks"
}
[/block]
Export Control checks can be integrated into a host system in any way described in [API usage scenarios for Export Controls](doc:api-usage-scenarios). Here, we focus on the peculiarities of Risk Assessment integration into Export Controls API.

First of all, the Risk Assessment integration should be activated and configured in the compliance profile used for the Export Control checks.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3419caa-ecWithRaIntegration.png",
        "ecWithRaIntegration.png",
        1587,
        832,
        "#dae1f0"
      ]
    }
  ]
}
[/block]
A user (order processor) of a host system creates or updates a business transaction (e.g., an order). The host system then calls, if all mandatory data was entered, a [checkTransaction()](ref:checktransaction) with a host-system-generated transactionId and requests Risk Assessment integration using the Export Controls API.

Export Controls performs all configured checks and creates a log entry. Also, during the Export Control check a new Risk Assessment questionnaire is created if it is needed according to the configuration in compliance profile and does not yet exist for the checked order. The result of the Risk Assessment integration is included in the Export Control check results under the Risk Assessment jurisdiction and could lead to a restriction, for example, due to an incomplete questionnaire. A response for the Export Control check is sent back to the host system. The host system processes the response results as defined by the [Export Control usage scenario](doc:api-usage-scenarios), e.g., it stores the results along with the order and blocks it in case of restrictions.

After the Risk Assessment questionnaire was created, a person responsible for completing the questionnaire, e.g., the order processor, can be notified via e-mail of the questionnaire to be filled in. The order processor can complete the questionnaire in the Risk Assessment web application. An export control officer can be notified via e-mail of the completed questionnaire. The status of the completed questionnaire will be considered during the next Export Control check. Either the order processor re-checks the order manually in the host system or the host system can receive synchronization events for changes in questionnaires. If the questionnaire was completed with critical status, it leads to a restriction for the Risk Assessment jurisdiction and should be evaluated by the export control officer, who can release the restriction with an approval in the Export Controls web application.
[block:callout]
{
  "type": "info",
  "body": "It is possible to use the synchronization API to receive synchronization events for changes in questionnaires. For more details see [About Synchronization API](doc:about-synchronization-api)."
}
[/block]
After the restrictions in the Export Control check transaction were processed by the export control officer, the order might need to be checked once more in the host system, depending on the implemented usage scenario. Depending on whether the export control officer approved the transaction, the result of the check might now turn into "not critical".