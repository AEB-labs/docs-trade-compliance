---
title: API Usage Scenarios
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: Read about the different scenarios in detail by following the links below
  pages:
    - slug: simple-screening
      title: Simple integrated screening
      type: basic
    - slug: screening-with-integrated-re-screen
      title: Screening with integrated re-screen
      type: basic
    - slug: screening-with-integrated-good-guy-definition
      title: Screening with integrated good guy definition
      type: basic
---
In the following pages, we demonstrate typical scenarios of how the Compliance Screening API may be called. The scenarios represent standard use cases which involve partner systems (e.g. ERP) that trigger the API calls and receive the respective response.

API calls to AEBs Compliance Screening require log in credentials. We have prepared a test system, which you can use for testing purposes for free. You can find more information on the required credentials under [The First Address Screening](https://trade-compliance.docs.developers.aeb.com/v4.1/update/docs/the-first-screening-of-an-address#/) .

We have prepared descriptions for three use cases:

<ul>
  <li>Simple integrated screening</li>
  <p>A simple integration which runs AEBs Compliance Screening on one or more addresses you would like to screen. The response may be processed by your partner system or you may be notified via e-mail. This lightweight integration use case would require subsequent action by a natural person through AEBs Compliance Screening GUI. </p>
  <li>Screening with integrated re-screen</li>
  <p>A standard integration which runs AEBs Compliance Screening. The response would be handled by the partner system, followed by subsequent action by a natural person through AEBs Compliance Screening GUI and a second screening triggered by the partner system to re-evaluate the screened addresses once more.</p>
  <li>Screening with integrated good guy definition</li>
  <p>A complex integration which runs AEBs Compliance Screening and allows to handle the response entirely through a partner system. This includes multiple individual API calls to different endpoints and therefor requires integration of different responses into a partner system.</p>
</ul>

### In case you missed it

AEBs Compliance Screening API offers two interfaces: [REST](https://trade-compliance.docs.developers.aeb.com/v4.1/update/reference#/) and [SOAP]() . The equivalent endpoints for both interfaces are mentioned in the following pages. The REST-specific endpoints are mentioned first.\
Depending on the number of addresses you want to screen and the information that is required for the partner system to run appropriate processes, we recommend you read [Bulk vs. Single Address Screening](doc:bulk-vs-single-address-screening).
When a screened address results in a potential match, action is required, which is referred to as [Match Handling and Good Guys](doc:restricted-party-lists).