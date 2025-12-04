---
title: Embedding the AEB GUI into Your Software
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
## General information about Compliance Screening applications

The AEB Compliance Screening API allows the use of Compliance Screening functionality not only in your own program code, but also to embed the GUI of Compliance Screening in your own software via UI APIs.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        API variant
      </th>

      <th style={{ textAlign: "left" }}>
        Link to documentation
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        REST
      </td>

      <td style={{ textAlign: "left" }}>
        [Compliance Screening Applications](ref:compliance-screening-applications)
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        SOAP
      </td>

      <td style={{ textAlign: "left" }}>
        <a href="https://rz3.aeb.de/test4ce/servlet/bf/RexAF?WSDL" target="_blank">RexAF (WSDL)</a>\ <a href="https://rz3.aeb.de/test4ce/servlet/bf/doc/RexAF/de/aeb/xnsg/rex/af/IRexAF.html" target="_blank">RexAF (JavaDoc)</a>
      </td>
    </tr>
  </tbody>
</Table>

A call to a UI API is technically a standard API call - the authentication process is the same, request parameters are transmitted as HTTP body. However, a UI API returns a link in the response, which the caller can open in a new browser window or in an embedded frame of the web application, allowing the user to access the desired Compliance Screening application.

More details on UI API requests can be found in [REST](ref:compliance-screening-applications) or <a href="https://rz3.aeb.de/test4ce/servlet/bf?lang=en" target="_blank">SOAP</a> documentation.
