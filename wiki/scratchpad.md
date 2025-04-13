---
title: Scratchpad
layout: default
excerpt: A scratchpad of notes from the lead dev
---

## About
This is a periodically-updated scratchpad for the primary developer. It's not automatically updated, it's just here to give a share vague concepts that have been considered.

# Disclaimer
**This is not a list of features to implement**, it exists to keep track of ideas to _research_. If anything listed below sounds like something that should get more attention, please make a feature request on the [Issues page](https://github.com/Frolic-chat/Frolic/issues)

## Scratchpad
```text
AUTOBUILD/CI

update electron version to something that works with kwallet6
*** update electron

Confront auto-ads
	investigate timer - is it broken?

StrangeStorage:
	Send Love function (👍/👎)
		How to manage sharing without storage server?
	Trans F/M state
	Pronouns/perception for H/S?
	HQ portrait
	Safe Word feature from april 1 post
		Enabled/Disabled state for each player
	Protocol exchange
		When someone starts typing at you you get a message, can we send something innocuous back to figure out if we should start protocol communication? Is there any other non-intrusive player-to-player communication to piggyback off of?
	Investigate storage options:
		EIcon???
		Inline image data (steganography)
		Profile image data (steganography or caption?)
		Contact info?
			rule: Only use completely irrelevant/dead
			AIM: aim:goim?screenname=<DATA>
			skype: skype:<DATA>?chat
			yahoo: ymsgr:sendIM?<DATA>
		groups
		channels
		can any of these be established from in chat?


Better use for side bar in PM than showing profile?

smart filter for blank/mostly empty profiles
	- empty avatar detection?
	- empty profile body?
	- lacking common/meaningful info?
	- lacking any customs

v - smart filter for hubs
--> receive feedback

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

shorten list of options above chats,
OR MOVE THE OPTIONS TO THE BOTTOM

Don't play noise for broadcast except in console

Chat window just for broadcast?

Recommendations on blank pm/button on pm
	- things to talk about when msging people
	- reminder to check their profile...?

PROFILE RECOMMENDATIONS:
	"use small/big instead of sub/sup in profiles"
	"SHORTEN YOUR DESCRTIPTION!"/use collapses
	keywords? A checklist a user can go through.
	invalid [color=] tags. - silver, grey, capitals - anything not a normal color

Build the "new notes" pop-up into the user list, since it's going to cover the bottom part of it anyways. Might as well allow users to scroll to the bottom of their user list without having to X the note pup-up.

Show neutral matches

Eidolons: Basic character matches vs Roleplay matches vs Vibe matches

extend friend/bm message notify to PMs; ie verify notify isn't singular controller of DMs.

Significantly redo notification settings for ✨ clarity ✨
	move to own settings window (when settings redo)

Dim characters who aren't friends of this character.
BM remembered by who you were on when you BMed them?

Manually tag players based on your interest in them

Reminders to add memos to players?

More prominent member logins (user icon?)

"Send love" dropdown that hides friend request, bookmark, send love, send note, etc.

Hide Search/Settings/Recent/Ad/PostAds/Helper behind dropdown menu.

flower icon change automatically

Icons except with checkbox - possible to change layout based on setting option?

friends as icons, profile mods as icons.

Single line PMs? First name only?

custom gender?

use notes for more shit

js for random colors

Relevant settings locations - is it possible to open the general settings to the appropriate page and section?

Character info popup sometimes uses wrong name. Needs to refresh when receiving character info.

Expected behavior of species:
	For multi-species detection:
	Look for ^ or , and match species after that until $ or , or ' and '

Remove "Status:" from ChatView

You can set an empty memo...

else if (this.profile.character.image_count > 1 && this.profile.character.image_count < 3)
logic wrong.

Stop filters from filtering chat or PM messages from room mods. - Temp exception list for each room?

"Browser settings" window is its own window!!!

move rising options out of their own submenu

Show f/m pref in character popup.
	This is in CharacterPreview.vue:376 but no obvious changes come to mind to fit the motif, "x-years-old bisexual male"

*** Theme capitalization -->> const name = `${speciesNames[speciesId].substring(0, 1).toUpperCase()}${speciesNames[speciesId].substring(1)}`;

lighten(), darken(), saturate() adjust-color()

nyehe, nuttoohard to expressions

Species:
	add "Room" to hub profiles
	add "shape changer" "Doppelganger" to shape shifter
	add "machinery .*"
	add 'shep' to dog
	add "varies" to ???
	"Felis Catus, American Bombay" is showing up as a canine
	"American Opossoum"

can upgrade sass now

three columns of pictures at wide screens
	one column for narrow screens

Check how iconification for rooms and PMs work when shrinking window.

MORE SORTING METHODS for channel members

hsl(231.4285714286, 14.8936170213%, 48.431372549%)
rgb(105, 110, 142)
#696E8E

round top right and bottom left of members list.
	border-radius-bottom-left: 3px;
	border-radius-top-right: more;

Move filtered members to the bottom of the member list
	Move "hidden" users to bottom of member list

@vue/runtime-dom

When localizing bbcode bar, use os_modifier_key instead of hardcoding Ctrl.
	https://github.com/Fchat-Horizon/Horizon/pull/62/commits/40b2ffe87536050cabe852f54d316dd02f66ffb0

Functions shouldn't be in the structure, they should be outside.

reconstruct EventBus to use -pre and -post

Investigate electron events for window gaining focus
Window.vue:404  -- window show - add event listener?
window.addEventListener('focus', func);
mainWindow.webContents.on( focus?

new ffxiv species kink match

"invalid ticket" means tooltip is stuck on loading forever.

eidol shortcut for "people who are into me" (ie pairing pref to match me, etc)

reexamine how species determination is done
	specifically, do/should we use .* in species names, or doe that break comma separating?

Commandline flag to run portable.
	Save/load settings to a selected directory.


Cuntboys kink is broken
	None gender kink is broken

"exotic species" kink match

orientation matcher only works for cis genders...
	Pansexual: return neutral
	f/m pref return early if they're f/m, even before checking your own gender

Add code to private messages to allow pinging for various things.
	Allow unread for chats

Custom theme for frolic

allow disabling pinged by bbcode

read eicons and stuff from text file

change gender sort to character preference.

columns of image should scale with app width

MOVE SIDEBAR INTO CONSOLE
	Console top bar size adjustment

Webpage features? Fix it up.

Setting "Show high quality ("Rising") portraits text explanation.

SettingsView exclamation mark errors.
UserView silly type errors.





move updating and external urls to a text file so people can edit it without updating

move log location file should also allow moving configuration files?? (for portable build)
	similar to "set default browser"
	settings in common.ts for system wide
		also check ./interfaces.ts
	SAVE SETTING WITH APP(?)
		also include a warning about password saving still being dependent on your OS/being saved with OS. Refrain from using Save Password (disable it?)
	Need fallback directory,
		and to notify user prominently if alternate directory is specified but unreachable.
```
