---
title: Scratchpad
layout: default
excerpt: A scratchpad of notes from the lead dev
---
# Scratchpad

## About
This is a periodically-updated scratchpad for the primary developer. It's not automatically updated, it's just here to give an idea of concepts that were thought of and may need to be looked into further to decide if they're a good fit for Frolic.

# Disclaimer
**This is not a list of features to implement**, it exists to keep track of ideas to _research_. If anything listed below sounds like something that should get more attention, please make a feature request on the [Issues page](https://github.com/Frolic-chat/Frolic/issues)

## Scratchpad
```text
AUTOBUILD/CI

Confront auto-ads
	investigate timer - is it broken?

StrangeStorage:
	Send Love function (👍/👎)
		For character
		For attributes on the profile (images, paras, customs)
		For messages during chat (IE "Love that post!")
		How to manage sharing without storage server?
	Trans F/M state
	Femboy
	Pronouns/perception for H/S?
	HQ portrait
	Duration
	Safe Word feature from april 1 post
		Enabled/Disabled state for each player
	Other custom pings in PMs:
		"Are you there?"
		Sticker protocol - Random snippets?
	Protocol exchange
		singular user channel for people to initiate conversations?
			would have to keep noise to a minimum
		When someone starts typing at you you get a message, can we send something innocuous back to figure out if we should start protocol communication? Is there any other non-intrusive player-to-player communication to piggyback off of?
		Encoded regular messages (a la OOC chat or Safeword)
	Investigate storage options:
		Profile
			Markup: Can use TAGS in [i=], etc, to demonstrate places.
				IE a [i=ads][/i] tag right before a collapse would show that collapse in a separate "ads" tab in the chat.
				BUILT IN GENERATOR TO CRAFT YOUR [i=][/i]
				Header for highly specific information? `x-hq-portrait=` for example?
		EIcon???
		[bbcode]?
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

		TEAL protocol:
		Text-Environment Augmentation Lexicon:
			Chat name color:	teal://name-color=#090909
			Rising Portrait:	teal://hq-portrait=https://...
			Start ad section:	teal://ad=Title?
			End ad section:		teal://ad=&&
			Hidden ad:			teal://hidden-ad=You can put anything but an end bracket here!
			Stackable:			teal://name-color=#090909&&hq-portrait=https://...&&hidden-ad=Hello!


Better use for side bar in PM than showing profile?

sticky image popup to different parts of screen.
	not covering user menu or member list

smart filter for blank/mostly empty profiles
	- empty avatar detection?
	- empty profile body?
	- lacking common/meaningful info?
	- lacking any customs

Match single species in faves as species of speciesless?

Smart filters:
	hubs
	poke/digi/moogles smart filter 	  	 --> canon species
	obesity/weight gain/eating disorders --> weight play
	new 								 --> nonbinary genders

prune long option lists

redo pack.js logic to accept command line arguments
	- needs redo mac section to parse signing name
	- need way to build appdmg
	- sort provided dev keys

https://github.com/electron/forge/issues/3371
https://github.com/LinusU/node-appdmg/issues/234
!!! python3 -m pip install setuptools !!!

research appimage metadata
https://github.com/AppImage/appimagetool

side bar on left has too many items, pushing my rooms and people down.

meld/side-by-side editing for creative writing.
shared editing page a la google docs

notify people that they're visible on the front page when they have the note-checker on.

disable save password and warn for no secret service available

Investigate the site session

autoupdater...
modern packager? Electron-Forge?

Safe image hosts:
	imgbb (ibb)
	imgbox
	postimage
	ImageShack
	ImgPile
	kek.gg

"Browser settings" window is its own window!!!

shorten list of options above chats,
OR MOVE THE OPTIONS TO THE BOTTOM

Recommendations on blank pm/button on pm
	- things to talk about when msging people
	- reminder to check their profile...?

Build the "new notes" pop-up into the user list, since it's going to cover the bottom part of it anyways. Might as well allow users to scroll to the bottom of their user list without having to X the note pup-up.

Show neutral matches

Eidolons: Basic character matches vs Roleplay matches vs Vibe matches

Manually tag players based on your interest in them

Significantly redo notification settings for ✨ clarity ✨
	move to own settings window (when settings redo)

extend friend/bm message notify to PMs; ie verify notify isn't singular controller of DMs.

Reminders to add memos to players?

More prominent member logins (user icon?)

"Send love" dropdown that hides friend request, bookmark, send love, send note, etc.

friends as icons, profile mods as icons (strangestorage?).

custom gender?

use notes for more shit

js for random colors

Relevant settings locations - is it possible to open the general settings to the appropriate page and section?

Character info popup sometimes uses wrong name. Needs to refresh when receiving character info.

Expected behavior of species:
	For multi-species detection:
	Look for ^ or , and match species after that until $ or , or ' and '

You can set an empty memo...

Stop filters from filtering chat or PM messages from room mods. - Temp exception list for each room?

Show f/m pref in character popup.
	This is in CharacterPreview.vue:376 but no obvious changes come to mind to fit the motif, "x-years-old bisexual male"

*** Theme capitalization -->> const name = `${speciesNames[speciesId].substring(0, 1).toUpperCase()}${speciesNames[speciesId].substring(1)}`;

lighten(), darken(), saturate() adjust-color()
can upgrade sass now

three columns of pictures at wide screens
	one column for narrow screens

MORE SORTING METHODS for channel members

hsl(231.4285714286, 14.8936170213%, 48.431372549%)
rgb(105, 110, 142)
#696E8E

round top right and bottom left of members list.
	border-radius-bottom-left: 3px;
	border-radius-top-right: more;

Move filtered members to the bottom of the member list
	Move "hidden" users to bottom of member list

When localizing bbcode bar, use os_modifier_key instead of hardcoding Ctrl.
	https://github.com/Fchat-Horizon/Horizon/pull/62/commits/40b2ffe87536050cabe852f54d316dd02f66ffb0

Functions shouldn't be in the structure, they should be outside.

reconstruct EventBus to use -pre and -post

"invalid ticket" means tooltip is stuck on loading forever.

eidol shortcut for "people who are into me" (ie pairing pref to match me, etc) - show passive search box

move log location file should also allow moving configuration files?? (for portable build)
	CHECK OUT: const baseDir = app.getPath('userData');
		it can accept 'exe'
		https://www.electronjs.org/docs/latest/api/app
	similar to "set default browser"
	settings in electron/common.ts for system wide
		also check ./interfaces.ts
	Commandline flag to run portable.
	SAVE SETTING WITH APP(?)
		also include a warning about password saving still being dependent on your OS/being saved with OS. Refrain from using Save Password (disable it?)
	Need fallback directory,
		advise user that not having a directory to save settings may result in unexpected behavior.
		The backup directory should be on the local directory, almost certainly the primary drive.
		Notify prominently in main app if alternate directory is specified but unreachable.
	Recommend turning off ad logging and channel logging to reduce writes.

close irrelevant chat messages
	"There are too many search results. please narrow your search."
	"There were no search results."

queue fs read/writing so it can be made concurrent
https://stackoverflow.com/questions/31978347/fs-writefile-in-a-promise-asynchronous-synchronous-stuff

read eicons and stuff from text file
	Right click eicon menu
	Favorite eicons are saved somewhere, investigate how for eicon category loading from file.

mounting imagepreview takes a while...

bad exotic creatures tooltip:
	exotic
new ffxiv species kink match

hardcoded colors in chatview

scrollbar on profile sidebar

highly X on tab when mousing over

top entry in PM list has rounded top corner, but icons aren't top aligned.
	set overflow: hidden; on <a> block

Remove `Contact details/Sites` column if no details/sites
	infotags.vue

support for additional contact info links
	ffxiv -> lodestone
	xbox live -> xbox profile
	WoW -> armory
	telegram -> open new PM link
	steam -> steam account page

COMBINE FRIENDS AND CHANNEL LIST

in-app notes
	text-box autosave/draft editor
	easy access to memo on that person
	make live -> note -> live easy
	can i use connection.queryApi ??????????

ENABLE ROAMING IN LOGIN

Frolic icon - multiple flowers blending together? Like one petal from each color.
		Like the old people holding hands ubuntu logo

getCharacterUrl(): string {
    return `flist-character://${this.character.name}`;
}

if ((<Error & {request?: object}>e).request !== undefined) {//catch axios network errors

Allow unread+mention status for PMs

Smart filter female, male, and nonbinary, via chat gender instead of character Gender.

RobustReminders
	A place where you can be reminded of things. Ie haven't changed password in 6 months. Person on personal-notify when you log in.
Serenity

DOCUMENT
OVERALL DESIGN PHILOSOPHY
	Friend focused
	Communication focused
	Powerful tools with simple interfaces
	Err on the side of user control (complexity), but a simple user should always be able to do *something*


Big features:
	Custom theme for frolic
		flower integration
	// to mean OOC - provide a uniform output
		grey text in double parenthesis??
	move updating and external urls to a text file so people can edit it without updating
	MOVE SIDEBAR INTO CONSOLE
		Console top bar size adjustment
	Settings groups:
		Notifications
		Serenity
			Sounds for specific events?
			Queue notifications (per channel?)
				Cooldown on channels? Per person???
			Way to see all channels with custom notification settings
			DND for certain time (like to watch a movie or something)
			Customize DND settings
			ROUTINE BASED sound/visual SETTINGS (night mode, etc)
			Visual options???
				high contrast
				reduced colors
				colorblind mode
		Personality
			Custom Chat Color
				also display own custom color on name in sidebar
			HQ Portrait
			Other enhancements
		Experiments
	PROFILE RECOMMENDATIONS:
		"use small/big instead of sub/sup in profiles"
		"SHORTEN YOUR DESCRTIPTION!"/use collapses
		keywords? A checklist a user can go through.
		use kinks appropriately ("all kinks are faves")

Small features:
	Warning on start if your log level is debug or worse
	Setting "Show high quality ("Rising") portraits text explanation.
	columns of image should scale with app width
	Highlight characters in friends list who are friends of **this** character
		BM remembered by who you were on when you BMed them?
	Species matching:
		Predator/Prey species ????
		Were/lycanthrope? 	445
		Move undead into undead 556

Bug fixes:
	allow disabling pinged by bbcode

Misc:
	website theming

Bring out personality, relationship, apparent age

The question for where something goes really is, how do I DO the things I want to do. Wanting to DO similar things should go to the similar place and each place should make sense for itself. Accessing search and eidols (passive search) together makes sense. Accessing eidol customization and ad editor also makes sense. How does it make sense to start running ads? What other ad-like behaviors do you want to be able to toggle on or off?
	What is the feeling I have? There should be the same way to satisfy it.
		If the feeling is desire for your friends, all friends access should be in the same place.
		If the feeling is desire for something new, all new-person hunting techniques should be in the same place.
```
