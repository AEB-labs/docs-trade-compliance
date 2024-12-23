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

Besides business facades (BF), which allow the use of Compliance Screening functionality in your own program code, the AEB Compliance Screening API also offers application facades (AF) to embed the GUI of Compliance Screening in your own software.

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        Technology
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
        [Compliance Screening Applications](ref:compliance-screening-applications-1)
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

An application facade call is technically a normal business facade call - the authentication process is the same, request parameters are transmitted as HTTP body. But an application facade returns a link in the response, which the caller of the application facade can open in a new browser window or in an embedded frame of the web application, so the desired application of Compliance Screening opens for the user.

More details on application facade requests can be found in [REST](ref:compliance-screening-applications-1) or <a href="https://rz3.aeb.de/test4ce/servlet/bf?lang=en" target="_blank">SOAP</a> documentation.
