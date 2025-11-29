---
title: StrangeStorage
layout: default
excerpt: A discussion of unusual ways to store data on F-List
---
# StrangeStorage

## Abstract
Below is a primer on ways to store arbitrary information on F-List, beginning with the most mundane and devolving into infinite insanity.

# Disclaimer
Using features on any website in a way not intended by the website owner can result in your ability to access the site becoming restricted. The discussion on this page is only that: discussion. It is not endorsement and does not offer any conclusion on appropriate ways to use websites.

## From the Scratchpad
Here are my initial notes on storing information in F-List profiles. You may use these notes to determine if you're interested in reading the rest of this.
```
StrangeStorage:
	Send Love function (👍/👎)
		For character
		For attributes on the profile (images, paras, customs)
		For messages during chat (IE "Love that post!")
		How to manage sharing without storage server?
	Trans F/M state
	Femboy
	Pronouns/perception for H/S?
	Partner preferences
	HQ portrait
	Safe Word feature from april 1 post
		Enabled/Disabled state for each player
	Protocol exchange
		When someone starts typing at you you get a message, can we send something innocuous back to figure out if we should start protocol communication? Is there any other non-intrusive player-to-player communication to piggyback off of?
	Investigate storage options:
		[bbcode]
		Can use TAGS in [i=], etc, to demonstrate places.
			IE a [i=ads][/i] tag right before a collapse would show that collapse in a separate "ads" tab in the chat.
		EIcon???
		Inline image data (steganography)
		Profile image data (steganography or caption?)
		Contact info?
			Rule: Only use completely irrelevant/dead
			Even so, appearance is intrusive, so does not solve the issue.
			AIM: aim:goim?screenname=<DATA>
			skype: skype:<DATA>?chat
			yahoo: ymsgr:sendIM?<DATA>
		groups
		channels
		can any of these be established from in chat?
```

## Introduction

### Reasons for Storing Data
Using F-List and its chat, F-Chat, for roleplay is not a perfect experience. There are faults both technical and prejudiced. There may be reasons you want to stash information in your profile for retrieval either by yourself or from someone else.

For yourself, you may want to store:
* details about your own character that you're uncertain about
* your previous ads that returned good results
* rewording for your profile that you haven't finished

For others, you may want to offer:
* whether your male character is masculine or feminine
* details on your preferences for other characters, such as only masculine women, Very Tall Squirrels (not naming names), whether you think kemonomimi are furries or humans, etc.
* which direction, if any, your transgender character is going
* are you willing to date a magic player or are you strictly a yugioh person
* mario party 2 or 3 this is going to determine if we can be friends or not

For a chat client like Frolic:
* a url of a high-quality avatar to display in place of F-List's 100x100 user avatars
* a custom name color to override the default gender-based colors
* ads that you dont want to display in your profile but still want people to find
* whether or not your chat client supports any other special features, such as safeword or custom chat<->chat communications like Send Love.

## Desired Attributes
What makes a *good* storage? There are a handful of factors that can make different ways of storing data more or less good.

### Desirable Behavior
* **Easy to implement**: The individual responsible for storing the data must be able to do so, understanding the steps to do so and the possibility of things that could go wrong, and how to fix them.

*  **Fast to implement**: When dealing with human-implemented data storage, the speed at which you can construct and implement the storage is a part of the "ease" - time consuming tasks are more difficult than momentary tasks for more people.

* **Easy to parse**: The program or person parsing the stored data must be able to do in a way that makes sense to them. For person-interpreted data, simple text in a known language makes sense. For computer-interpreted data, data that can be identified and parsed with pattern-matching is a large benefit.

* **Fast to parse**: An application that runs sluggishly can give a negative impression to the user even if the application has very advanced functionality.

* **Lightly encoded**: Encoding data can make its footprint smaller, which is desirable with data sent over the internet.

  Text fields have more storage opportunities than binary data, especially in our scenarios. Therefore, quality binary-to-text encoding is highly desirable if operating with binary data.

  Documentation on the sort of encoding you do is highly desirable to avoid suspicion. If multiple sources can independently verify what your encoded data decodes to, that's a good sign. The less computation necessary to decode, the better.

* **Clarity**: Having different data fields clearly delimited in an unencoded format can help with readability.

* **Namepsacing & Versioning**: In a broader sense, "technical clarity" keeps data relevant over long periods of time, even after considerable changes.

* **Does not interrupt the normal flow of information**: Data storage that doesn't interfere with normal comprehension is best, when trying to store data to be interpreted by an app.

### Undesirable Behavior
* **Encrypted or heavily encoded**: Encrypted data in any form is suspicious despite the fact that anything, including _lorem ipsum_, can be encrypted.

  On top of that, it's **highly** suspect to encrypt any information that's expected to be publicly interpreted. If you want people to read it, why would you go through the effort to obfuscate it?

  For information that's _not_ supposed to be publicly interpreted, you should just avoid publishing the data at all, rather than doing so in an encrypted format. Any data you submit to the internet should be considered visible to _someone_, _somewhere_. (Probably the NSA.)

  For _encoded_ (not _encrypted_) data, using advanced forms of data storage, such as compression or cryptic translation, is also suspect _not_ because of an inherent danger, but because of the _appearance_ of danger. If your data is inoccuous, it should present itself as innocuous.

  Encoding that formats the data in a way a user cannot understand means accidental loss of data can't be easily discovered. For example, in these two cases:

  ```
  xn--6-i4bu
  xn--9-fht8
  xn--2-1a60

  M-FM-I*M-^_vv[2R^MM-^NM-mM-ffM-^W%^_?M-7M-t\(M-=U5]M-)0M-WM-?^EM-H^^sRM-^W1M-
  ^]lM-^OM-?zM-,M-RM-N^TTM-CM-^MM-}M-m'M-+M-^BM-uM-^\M-w(<M-^VM-dM-^TFM-^VM-TM-
  VM-NRBM-^?}YM-^ZH^RvM-^I^@M-u^HgY))M-^GM-^HklRM-FM-OM-u^R-^@>M-">r^B|M-HM-OM-
  ```

  In the first case, clear delineation of the fields and an obvious header make the data easier to glance over. It would be easy to notice if the beginning or end of the string was missing, or even digit field in the middle.

  In the second case, a lack of meaningful beginning or clear distinction between data types or fields means we can't be certain the message is intact until we try to decode it.


## Ways to Store Data

### Dead Simple
Put it privately in your own character's memo. You can include text, links, or any information that can be encoded as text.

Put it publicly in your profile, custom kinks, or character info fields. You can print text, links, or any information that can be encoded as text.

   You can change the color of information to make it harder to read.

### Still Ordinary
Send it to yourself as a note.

Create nested collapses on your profile containing as many details as you want, now organized in a tree-structure.

Create a secondary profile for details not immediately necessary but still relevant, such as world or plot details you want to indulge in.

### Sane
Create a private chat room in F-Chat to host information in the description. Information typed into the text box will be saved to your local logs (if using a log-supporting client).

It will also be shared only with the people in the room at the time you typed it. This is an interesting aspect of storing shared-data and should be kept in mind.

Your private chat can be made public or invite-only to share your information with friends. This has the added benefit of allowing them to participate with your information. It also means people can "sign up" to receive your data. (Like a mailing list!)

All that to say this is, effectively, just a bad version of Discord.

### Not That Crazy
Putting cryptic information directly in your profile, tucked away in collapses, not intended to be read by a human.

[[--unfinished--]]
