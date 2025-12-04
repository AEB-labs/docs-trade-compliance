---
title: Basic Concepts
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
Risk Assessment is integrated into Export Control checks (API function [checkTransaction()](ref:checktransaction)) as a separate jurisdiction.

> 📘 Jurisdiction “Risk Assessment” is available for configuration in the compliance profile (in a separate sheet) if Export Controls and Risk Assessment are licensed for the client.

There are 3 basic conditions (gates) to be met for Risk Assessment integration:

**Gate 1**: Risk Assessment integration must be activated in the compliance profile used for the Export Control checks. If this is not the case, the Risk Assessment jurisdiction is not included in the check result of the Export Control check.\
**Gate 2**: Risk Assessment integration must be requested in API function [checkTransaction()](ref:checktransaction). If this is not the case, the Risk Assessment jurisdiction is included in the check result, but only with the information that Risk Assessment integration was not requested.\
**Gate 3**: In the compliance profile used for Export Control checks it is possible to define manual restrictions for the Risk Assessment integration to limit for which business transactions the integration should be performed. If manual restrictions are in place, the Risk Assessment integration will only be considered as relevant if at least one of these manual restrictions is applicable to a business transaction (at least for one of its items). If this is not the case, the Risk Assessment jurisdiction is included in the check result, but only with the information that Risk Assessment integration is not relevant for the transaction. If no restrictions are listed in the compliance profile, the Risk Assessment integration will always be considered as relevant.

## What happens when Risk Assessment integration is enabled for an Export Control check?

During an Export Control check with enabled Risk Assessment integration (API function [checkTransaction()](ref:checktransaction)), a Risk Assessment questionnaire is created for a checked business transaction (e.g., order) if it is needed according to the configuration and does not yet exist (see [Reference Data](doc:reference-data)). This leads to a restriction for the Risk Assessment jurisdiction in the check result. If the questionnaire already exists, its result is evaluated and considered in the check result. 

> 📘 At any moment at most one questionnaire can exist for a single business transaction from a partner system (the newest one is always the relevant one).

The following check results are available for the Risk Assessment jurisdiction:

<Table align={["left","left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        Result
      </th>

      <th style={{ textAlign: "left" }}>
        Description
      </th>

      <th style={{ textAlign: "left" }}>
        Next Steps
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        OK
      </td>

      <td style={{ textAlign: "left" }}>
        The questionnaire has been completed with an uncritical result.
      </td>

      <td style={{ textAlign: "left" }}>
        No further actions are needed.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        INFO
      </td>

      <td style={{ textAlign: "left" }}>
        No questionnaire is required for the business transaction.
      </td>

      <td style={{ textAlign: "left" }}>
        No further actions are needed.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        CLEARED
      </td>

      <td style={{ textAlign: "left" }}>
        The result was initially critical but was released with an approval.
      </td>

      <td style={{ textAlign: "left" }}>
        No further actions are needed.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        CHECK
      </td>

      <td style={{ textAlign: "left" }}>
        The questionnaire exists, but has not been completed yet.

        Or a questionnaire is required, but could not be yet created, because the transaction data is marked as "not complete for Risk Assessment".
      </td>

      <td style={{ textAlign: "left" }}>
        The questionnaire needs to be completed or an export control officer could clear this result with an approval.

        In the business transaction in the partner system all necessary data for questionnaire creation should be filled.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        RESTRICTION
      </td>

      <td style={{ textAlign: "left" }}>
        The questionnaire was closed with a critical result.
      </td>

      <td style={{ textAlign: "left" }}>
        An export control officer could clear this result with an approval.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        ERROR
      </td>

      <td style={{ textAlign: "left" }}>
        The questionnaire could not be created due to an error (technical error or incorrect data such as incorrect questionnaire template).
      </td>

      <td style={{ textAlign: "left" }}>
        Check the logs to get more information about the reason for the error.
      </td>
    </tr>
  </tbody>
</Table>

## Is the Risk Assessment integration into Export Control checks transaction- or item-specific?

A questionnaire is created for the business transaction as a whole, not for each item. The following data from the business transaction is used to create a questionnaire (in addition to the data, that is explicitly forwarded for the questionnaire creation in the API call):

* Reference fields of the questionnaire (Reference and Reference (intern)) are filled with identification data of the business transaction (resp. transactionLabelHost and transactionIdHost).
* The order number of the questionnaire is filled from the order number of the first item of the business transaction.
* The company of the questionnaire’s user is filled with the company of the seller from the first item of the business transaction.
* All partners with their respective roles from all items of the business transaction (the duplicates are eliminated) are considered for the questionnaire.

> 📘 Risk Assessment partner roles could differ from Export Controls partner roles. Therefore, it is necessary to define the mapping between Export Controls partner roles and Risk Assessment partner roles in Trade Compliance Management (*Office – Master data – Partner roles*). For predefined partner roles this is already configured by default.

Since the Export Control check is carried out item by item, the Risk Assessment results are included in the check results for each item (except BOM items). However, the result for the Risk Assessment jurisdiction is identical for all items in one business transaction (except if some items are already released, while others are not).

## What happens if a business transaction to be checked changes and a questionnaire already exists?

If a questionnaire already exists, the data of the questionnaire is compared to the data of the business transaction to be checked. The comparison currently includes only the business partners.

If there are discrepancies, a person responsible for the questionnaire (a questionnaire’s user) is notified by e-mail. If no e-mail address is stored in the questionnaire, a warning is generated in the technical logs.

Thus, there is no automatic update of the questionnaire data (and no automatic deletion of the questionnaire), but  the e-mail about discrepancies contains the deltas. The questionnaire’s user must then update the questionnaire manually or delete/invalidate the questionnaire and trigger a new Export Control check, which then creates a new questionnaire with the current data.

## How do approvals work for the Risk Assessment jurisdiction?

Restrictions in the Risk Assessment jurisdiction can be released with approvals in the Export Controls web application, in the same way as for other jurisdictions. But approvals for the Risk Assessment jurisdiction also have some special features:

* Partial approvals are not supported for the Risk Assessment jurisdiction. A questionnaire refers to a concrete business transaction. Therefore, the (main) approval for an original business transaction (e.g., order) cannot be used as a basis for a (partial) approval of a subsequent transaction (e.g., delivery).
* If approvals for the Risk Assessment jurisdiction no longer match the most recent questionnaire for a business transaction, they are deleted automatically during an Export Control check. This prevents that the restriction in the Risk Assessment jurisdiction continues to be released, even though the reason for the restriction has changed and must be re-evaluated.

In the following cases, approvals are deleted automatically:

* Approvals for the Risk Assessment jurisdiction store the questionnaire the approval was created for (approvals without questionnaire data are also possible). If - meanwhile - a different questionnaire was created for a business transaction to be checked, then the approval for the old questionnaire will be deleted.
* Approvals for the Risk Assessment jurisdiction also store the state of a questionnaire at the time when the approval was created. If the state of the questionnaire - meanwhile - has changed (because the questionnaire was completed), the approval with the old state will be deleted. Other changes to the content of the questionnaire (except for completion) do not play a role, so they do not lead to the deletion of the approvals.
