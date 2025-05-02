---
title: Changelog
layout: default
excerpt: All release notes in one easy to find place.
---
# Changelog

## Next?
* Teal . . .
* Eidols . . .
* Home . . .

## Release 0.7.2
* Bugfix: Don't play broadcast noise for every open tab!!!!! I'm serious!!!!!!!!!!
* Broadcasts are only logged in the console.
* Broadcasts won't play in private messages. Added an option to enable that if you want it.
* Profile Helper now checks for inappropriate color tags, including the incorrect gray/grey... uh, which one was it?
* The "open conversation" dialog will now hijack your text input so you can start typing into it immediately.
* Additionally, you can use the Enter key to submit your query instead of having to hit the button.
* Internal debug tool set to speed up testing
* Default EIcon adjustments
* Species refinements and "divinitys" plural fix.
* Bugfix: Profile helper only recommended adding more images to characters with exactly 2 images. Now it also recommends it to characters who have only a single image as well.
* Speed-ups to URL handling and other under-the-hood fixes

## Release 0.7.0
* Orientation matching improvements for nonbinary genders, with further experimental improvements locked behind a toggle in the options
* Updated the room member list sorting button so people realize they can sort the room member list
* Member list gender sorting now uses your character orientation to put your prefered genders on top, instead of using a predefined order
* Updated the eicon pages to remove dead icons and include a wider variety of icons
* Significant updates to species lists, including adding "exotic species"
* Moved documentation to [its own site](https://frolic-chat.github.io/)
* Improvements to notifications for friend logins.
* Large localization update.

## Release 0.6.0
* Added setting to receive notifications when friends/bookmarks log in
* Added setting to receive notifications when friends/bookmarks send a message in a channel (configurable per-channel!)
* Notification settings with similar purpose have been grouped together. Further adjustments are still needed to the overall settings layout.
* The adblocker for the image popup works now!
* The channel member list and friends list no longer wig out when moving between PMs and channels
* Broken YouTube proxy removed; videos will play in the popup now, but they play muted 😒
* Alternative themes had their colors updated
* Fixed a bug where notechecker would still check for notes even if it was disabled
* Touch-ups to Kemonomimi matching
* Quieted some spammy application logs
* Updates to backend components
* Moved some fixed strings into the localization database.

Thank you to [FatCatClient](https://github.com/FatCatClient) for their contributions to keeping F-Chat up to date with modern features.


## Release 0.5.0
* Kemonomimi now match much more favorably in many circumstances. See the [Pull Request](https://github.com/Frolic-chat/Frolic/pull/3) for details.
* Adjustments to species categories in preparation for hybrid-species matching improvements
* Fixed a rare log-deletion oversight from vanilla F-Chat.
* Empty species are no longer considered human by default; they need some kind of decisive indicator such as "Humans Only" partner preference.
* Build fixes in preparation for Electron update

For legacy F-Chat Rising changelogs, see the [legacy changelog](https://github.com/Frolic-chat/Frolic/blob/master/CHANGELOG-legacy.md)
