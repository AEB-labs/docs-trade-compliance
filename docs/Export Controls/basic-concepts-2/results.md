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
        Next steps
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        **INFO**
      </td>

      <td style={{ textAlign: "left" }}>
        Some information was generated, but no restrictions apply to the transaction.
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction/order can be processed/exported.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **OK**
      </td>

      <td style={{ textAlign: "left" }}>
        No restrictions apply to the transaction.
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction/order can be processed/exported.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **CLEARED**
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction was initially critical, but was cleared either automatically or by a manual intervention from the export control officer.
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction/order can be processed/exported.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **CHECK**
      </td>

      <td style={{ textAlign: "left" }}>
        There is at least one manual intervention needed.
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction/order should be blocked until it gets cleared by the export control officer.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **REQUIRE**
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction requires a license for at least one jurisdiction.
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction/order should be blocked until it gets cleared by the export control officer.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **CUSTOM\_RESTRICTION**
      </td>

      <td style={{ textAlign: "left" }}>
        A *manual restriction* prohibits the export.
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction/order should be blocked.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **RESTRICTION**
      </td>

      <td style={{ textAlign: "left" }}>
        The export is restricted due to an embargo or similar reason.
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction/order should be blocked.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **ERROR**
      </td>

      <td style={{ textAlign: "left" }}>
        The check could not be performed for certain reasons, e.g., missing required data.
      </td>

      <td style={{ textAlign: "left" }}>
        The transaction/order should be blocked.\
        Check the response details of the request to get more information about the reason for the error.
      </td>
    </tr>
  </tbody>
</Table>

> 📘 To check if a transaction was cleared after a manual intervention by the export control officer within the *Export Controls* web application, a new call to checkTransaction() with the previously used **transactionid** has to be performed.
