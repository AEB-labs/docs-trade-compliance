---
title: Screening with integrated re-screen
deprecated: false
hidden: false
metadata:
  robots: index
---
Next up is the most common integration, which consists of two individual calls to AEBs Compliance Screening API. The results from the initial screening call is typically evaluated and acted upon by a *Compliance Officer*.

<Image align="center" src="https://files.readme.io/ba8888d03fe22972c75d16705d9d5e1eeb1556439540745cfec0c21c08995a41-Slide4.JPG" />

### Step 1

In this scenario, a user starts by providing all relevant information to their partner system and triggers an API call to AEB Compliance Screening (either using the screenAddresses or the batchMatch endpoint). This will trigger AEBs address screening algorithm and check all supplied addresses. The partner system will receive a response with the information which addresses resulted in potential address matches, which in turn should block any associated transaction or business partner and further processing of such transaction.

### Step 2

The user will then evaluate all address matches in AEB Compliance Screening. This is usually done through AEBs Compliance Screening GUI. For address matches that are found to be false positives, “Good Guys” can be created.

### Step 3

Once all address matches are handled, a re-screen can be triggered, either by a user directly or through an automated configuration in the partner system and the response with no further address matches found releases previously blocked transactions.