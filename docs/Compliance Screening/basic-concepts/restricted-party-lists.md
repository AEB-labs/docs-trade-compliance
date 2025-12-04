---
title: Match Handling and Good Guys
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
Due to the complexity of identity matching and the often incomplete data provided by restricted party lists, the address screening can only provide a list of possible matches. Deciding whether the matches found really correspond with the entity screened often requires additional investigation by a user. This is called "match handling".

When match handling reveals that all the restricted party addresses found for the screened entity are mere name similarities and no real matches, the originally checked address can be defined as a Good Guy. If an address that has already been defined as a Good Guy is checked again, no matches will be found anymore. However, the [Bulk address screening](doc:bulk-address-screening) will report that the checked address is known as a Good Guy. 

> 📘 Good guys are also organized in lists (Good Guy lists). The Good Guy lists to be considered in address screening can be configured in the Compliance profile.

## Match handling and Good Guy definition in Trade Compliance Management

The entire process of match handling and Good Guy definition can be handled directly in the Trade Compliance Management web application.

So how could it work with address screening from partner system and match handling in Trade Compliance Management? 
For example: If a business partner has been checked from within your partner system and been returned as critical, 
you might set a block in this business partner or the affected order in the partner system to prevent that business is done with them for a while. 
A user or compliance officer will process this match in the special "Match handling" view in Trade Compliance Management. 
In this view, it is possible to define a Good Guy for the investigated match after an appropriate analysis or to mark this match as processed without a Good Guy definition. 
The second option means that the checked address really corresponds with the restricted party addresses found and the block for the checked business partner or affected order should be kept in the partner system (the next screening of this business partner will again return a critical result). 
If a Good Guy has been defined for the match, this means that the checked address is only similar to the restricted party addresses found and should be evaluated as uncritical in the next address screening. 
When the business partner is checked once again in the partner system, it will be recognized as a Good Guy and the check result will be uncritical and the business partner or affected order in the partner system could be unblocked.

If this workflow fulfills the needs of your company, the process of match handling in the partner system will not be needed at all. Only the blocking logic should be implemented if needed and repeated calls for address screening.

## Match handling and Good Guy definition in partner system

You can also develop the views and logic to allow users to do match handling and Good Guy definition within your software.

There are several API requests which can support users with match handling in the partner system:

* The request [Find matching addresses](doc:single-address-screening) could be used to get the matching restricted party addresses for a checked address. These matching addresses could be displayed to the user in such a way that the user can compare the checked address with the restricted party addresses found and then decide if the found addresses are real matches or not.
* If the user needs more details on a specific matching restricted party address, an API request can be used, which returns a URL for displaying details about that address, see [here](doc:embeded-aeb-gui-into-your-software). The URL could be opened in a browser window or could be embedded in a frame in the web application.

When match handling reveals that a screened address should be defined as a Good Guy, the partner system should make the request [Define a Good Guy](doc:define-a-good-guy). 
In this request, the address data provided by the partner system is transferred to the Good Guy that will be saved in the Trade Compliance Management system. 
If an address that has been defined as a Good guy is checked again, no matches will be found for this address anymore.
