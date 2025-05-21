---
title: Simple integrated screening
deprecated: false
hidden: false
metadata:
  robots: index
---
Let's start with a simple use case for running compliance screenings, in which a partner system calls AEBs Compliance Screening API once and the result is evaluated and acted upon by a *Compliance Officer*.

<Image align="center" className="border" border={true} width="123% " src="https://files.readme.io/f7241cfa2650ddac7da0bd16b706738c777d8a1573c4ab4319868f55c7a908f3-Slide1.JPG" />

![](https://files.readme.io/1aa447fbe2d22dba8245ac7312914486591f8bfc63cd53c63e17c9e0575da5f5-image.png)

In this scenario, a user starts by providing all relevant information to their partner system. Once finalised, the user can trigger an API call to AEB Compliance Screening (either using the screenAddresses or the batchMatch endpoint).\
This will trigger the address screening algorithm and check all supplied addresses against licensed restricted party lists with the results being logged automatically. The partner system will show whether a potential address match has been found or not.

After the user has evaluated all relevant information, they can either define “Good Guys” for false positive address matches or take internally defined actions on restricted business partners. “Good Guys” can be defined through API calls using the goodGuy endpoint, which will create “Good Guys” and log their creation. Once any potential match has been handled accordingly, the partner system triggers another API call to re-screen any blocked address, which returns with no further address matches found and therefore blocked transactions may proceed.