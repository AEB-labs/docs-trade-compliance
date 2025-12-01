---
title: Getting Started
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
  pages:
    - type: basic
      slug: using-the-data-feed-api
      title: Retrieving Data Subscription Files via API
---
_Data subscriptions_ allow you to retrieve a set of defined data from the Trade Compliance Management system on a regular basis.
This can be useful, for example, to store log entries from Compliance Screening in your own systems for further analysis or reporting.
While data subscription files can be retrieved via the Trade Compliance Management web application, this documentation covers the setup and retrieval via API.
If you wish to retrieve data subscription files via SFTP, please contact <Anchor label="AEB Support" target="_blank" href="https://service.aeb.com/hc/en-us/requests/new">AEB Support</Anchor>.

> 📘 Currently, data subscriptions are available for compliance log entries for address and Good Guy checks as well as for non-match log entries from non-match files.

The configuration of data subscriptions is done in the Trade Compliance Management web application.
The following steps guide you through the process:

### Step 1: Configure a partner system subscription

Before you can receive data from data subscriptions via API, you need to configure a partner system subscription.
Navigate to _Office_ – _Administration_ – _Synchronisation_ – _Partner system subscriptions_ and create a new entry
for your partner system.
Here, an ID of the partner system must be specified, which has to match the ID used in the API calls to retrieve the exported data files.
Futhermore, _Subscription file_ must be selected as subscribed object.

### Step 2: Create a data extract definition

Data extracts define the source object, extraction level (e.g., type of log entries), export format (CSV, JSON, or XML), and the fields to include in the subscription files.
For more information, see <Anchor label="Maintaining data extract definitions" target="_blank" href="https://docs.aeb.com/doc/cm-118677643-924124043-en-US/t-924124043-1050084491-en-US">Maintaining data extract definitions</Anchor> in the AEB docs.

> 👍 Make sure to select all relevant fields in the _Field selection_ sheet. These fields will be included in the exported data files.

### Step 3: Create a data subscription

Data subscriptions specify, among other details, the schedule for data extraction and a filter to select only the relevant data.
More information can be found in <Anchor label="Maintaining data subscriptions" target="_blank" href="https://docs.aeb.com/doc/cm-118677643-924124043-en-US/t-924124043-1050084491-en-US">Maintaining data subscriptions</Anchor> in the AEB docs.

> 🚧 Set a sufficiently large _Waiting time_ because subsequent changes to already extracted data will not be included in future exports.
> We recommend 10-15 days.

<br />
