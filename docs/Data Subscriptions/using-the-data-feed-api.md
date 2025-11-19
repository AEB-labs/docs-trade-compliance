---
title: 'Retrieving Data Subscription Files via API'
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
This page describes how to retrieve data subscription files from the Trade Compliance Management API.
The Data Feed API provides three endpoints that you need to implement in your client:

* [getPublishedDataFeedParts()](ref:getpublisheddatafeedparts): Poll for newly published data feed parts
* [dataFeedParts/{client}/{id}](ref:getdatafeedpartcontentforrest): Download the content of data feed parts
* [acknowledgePublishedDataFeedParts()](ref:acknowledgepublisheddatafeedparts): Acknowledge the successful processing of data feed parts

> 📘 The Data Feed API is also available as [SOAP-API](https://rz3.aeb.de/test4ce/servlet/bf/doc/DataFeedBF/de/aeb/xnsg/foundation/bf/IDataFeedBF.html).

### Prerequisites

To use the Data Feed API, you need to have configured data subscriptions and a partner system subscription in the Trade Compliance Management web application.,
see [Getting Started](doc:getting-started) for more information.

### Step 1: Poll for published data feed parts

Use the API method [getPublishedDataFeedParts()](ref:getpublisheddatafeedparts) to poll metadata about the next published data feed parts.
The response always contains the retrieval information for up to the next 10 published data feed files.

> 🚧 Make sure to use the correct partner system ID (`clientSystemId` field) in the request, as configured in the partner system subscription.

The response contains, among other data, an array of data feed part metadata objects, each containing a unique ID (`dataFeedPartId` field) that 
you will need to download the actual data feed part content in the next step.
Furthermore, the response includes a `syncId` field that is used to acknowledge the successful processing of the data feed parts in Step 3.

### Step 2: Download data feed part content

For each data feed part metadata object received in Step 1, use the API method [dataFeedParts/{client}/{id}](ref:getdatafeedpartcontentforrest)
to download the actual content of the data feed part. 
Use the ID of your client as the `{client}` and the `dataFeedPartId` field of the data feed part metadata object as the `{id}` path parameter.
The response contains the content of the data feed part file in the format specified in the data extract definition (CSV, JSON, or XML).

### Step 3: Acknowledge processed data feed parts

After successfully processing the downloaded data feed parts, use the API method [acknowledgePublishedDataFeedParts()](ref:acknowledgepublisheddatafeedparts)
to acknowledge their successful processing.
This will prevent the same data feed parts from being returned again in future calls to `getPublishedDataFeedParts()`.
In the request body, provide the `syncId` received in Step 1.

> 🚧 Make sure to use the correct partner system ID (`clientSystemId` field) in the request, as configured in the partner system subscription.