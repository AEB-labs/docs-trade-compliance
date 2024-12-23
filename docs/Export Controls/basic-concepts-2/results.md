---
title: Results
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
A check transaction consists of multiple check steps. These steps can be reviewed in the Export Controls web application.

The total **result** of a check transaction is the accumulated result of all check item results and can have one of the following values:
[block:parameters]
{
  "data": {
    "h-0": "Result",
    "h-1": "Description",
    "h-2": "Next steps",
    "0-0": "**INFO**",
    "1-0": "**OK**",
    "1-2": "The transaction/order can be processed/exported.",
    "1-1": "No restrictions apply to the transaction.",
    "3-0": "**CHECK**",
    "2-0": "**CLEARED**",
    "4-0": "**REQUIRE**",
    "5-0": "**CUSTOM_RESTRICTION**",
    "6-0": "**RESTRICTION**",
    "7-0": "**ERROR**",
    "7-1": "The check could not be performed for certain reasons, e.g., missing required data.",
    "7-2": "The transaction/order should be blocked. \nCheck the response details of the request to get more information about the reason for the error.",
    "0-1": "Some information was generated, but no restrictions apply to the transaction.",
    "0-2": "The transaction/order can be processed/exported.",
    "4-2": "The transaction/order should be blocked until it gets cleared by the export control officer.",
    "4-1": "The transaction requires a license for at least one jurisdiction.",
    "2-1": "The transaction was initially critical, but was cleared either automatically or by a manual intervention from the export control officer.",
    "2-2": "The transaction/order can be processed/exported.",
    "3-1": "There is at least one manual intervention needed.",
    "3-2": "The transaction/order should be blocked until it gets cleared by the export control officer.",
    "5-1": "A *manual restriction* prohibits the export.",
    "6-1": "The export is restricted due to an embargo or similar reason.",
    "5-2": "The transaction/order should be blocked.",
    "6-2": "The transaction/order should be blocked."
  },
  "cols": 3,
  "rows": 8
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "To check if a transaction was cleared after a manual intervention by the export control officer within the *Export Controls* web application, a new call to checkTransaction() with the previously used **transactionid** has to be performed."
}
[/block]