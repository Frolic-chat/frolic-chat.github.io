---
title: Changelog
layout: default
excerpt: All release notes in one easy to find place.
---
# Changelog

### Next?
* Enhanced matching
* In-app note RP

## Release 0.7.9
This is a minor bug-fix patch. Please see the 0.7.8 patch notes for recent features.

* Channel logging is now on by default

  **If you logged into a character during 0.7.8,** it may be off for that character. Please check the characters you've played to make sure channel logging is set to the setting you want. Characters you haven't logged into yet will default to `on`.

  This won't be an issue going forward as there will be as logging settings will apply account wide.

* Phrasing change on the login screen: "Username" -> "Account" for clarity

* Bugfix: "Close to tray" actually closes to the tray instead of exiting

* Bugfix: Filterable menu can actually be filtered instead of closing when you tried to click on the filter input

* Bugfix: Invisible error on the log viewer from the login screen

* Behind the scenes fixes for stability

## Release 0.7.8
* Accidental clicks on links and buttons when trying to close the right-click menu will be eaten

* Improved age matching against emojis to help you avoid *bad matches*

* The image preview should no longer show you a download dialog when presented with files

* Using Ctrl+Tab and Shift+Ctrl+Tab to switch between your characters no longer randomly stops working

* Fewer text boxes should have completely unnecessary scroll bars when using a custom font size

* Limited the memo to one line in the character preview to fit more information

* Character search no longer sometimes provides a mysterious source of lag by running in the background forever

* Added description to the "Import" settings tab

* Backend updates to make upgrades easier

* **Custom browser:**

  * "Default browser" settings are now "custom browser" settings

  * Fixed a variety of bugs related to opening external links and the custom browser settings

  * You can do some very interesting things if you're willing to get technical! To understand how to configure your own custom browser settings, visit the [Custom Browser Settings feature page](https://frolic-chat.github.io/wiki/features/browser-settings.html)

  * **Incognito Mode:**

    * A custom browser must be chosen to use "Open in Incognito mode" in the right-click context menu

    * "Open in Incognito mode" is now available on linux

    * Added a section in the custom browser settings to customize arguments for incognito mode

* **Profile Images:**

  * Adjusted the images tab on profiles to fit more thumbnails

  * Clicking an image will open a full-screen version of that image. Click anywhere to close.

  * Images now have a right-click context menu allowing you to: copy image url; open in browser; open in browser with incognito mode.

* **Smart Filters:**

  * Previously, the settings were bugged and applied whether or not you saved them, now they only save when you confirm.

  * Can no longer hide the owner and moderators from the channel member list

  * Can no longer hide channel messages and member list visibility of the owner and moderators *(Global moderators have always been exempt from filters.)*

  * A kemomimi's human/furry leaning will be used when determining whether they're hidden by the "hide furries" and "hide humans" options. Therefore, human-leaning kemomimi will still appear if you have furries hidden and vice versa.

  * Smartfilters should do a much better job of blocking new private messages

  * New players won't have autoreply enabled by default anymore

  * "Intersex" is now "Nonbinary" in the settings; functionality is unchanged

* **Conversations:**

  * New setting to require a *second* Enter press to send a message, for those with fast or clumsy fingers (*guilty as charged...*)

    A visual effect around the chat input box will appear to let you know you can send your message. It will expire after 3 seconds.

  * Open conversations no longer show a close button when they're pinned; you must first un-pin the conversation to close it

  * Scroll to the bottom of a conversation by hitting Escape

* **Channel ads:**

  Channel ads have been unsupported for a *very* long time. Automatic ad posting is supported via the sidebar above your channels and PMs.

  This update implements changes to minimize the old system's impact and prepare for its removal.

  * Disabled creating new channel ads

  * Disabled posting channel ads

    *Migrating channel ads to the global ad system is still supported. Please use this feature while it's available.*

  * Collapsed the UI buttons for channel ads into a single button

  * Hide options that aren't relevant

    (For example, characters that don't have channel ads to migrate won't be able to open the channel ads menu)

* **Channels:**

  * You can now disable channel logging while still logging private messages

  * Switching channels is much smoother

  * Characters in the channel list update much more responsively when they change (such as changing status, being matched by a filter, or being promoted or demoted)

  * A horizontal scrollbar should no longer appear on member lists with long character names

  * There's a new option to enable loading matcher/filter data for every character in a channel. You can find it in the General section of settings.

    *Warning:* Because this option loads many more characters than usual, it carries a label advising that your system have adequate system memory.

    Characters are only loaded from the on-disk cache, so this won't burn through your bandwidth or overload the server - but it also means characters you've never seen before won't have matcher/filter data displayed until you interact with them.

    Currently this must be enabled on a per-character basis. Next update, it will be part of the app-wide settings.

* **Experimental:** We're testing a new method of the "high-quality portraits" feature. This method will let you hide your custom avatar url so your profile flow goes undisturbed.

  To make it very simple, visit the settings! There's a new tab that will help you format your link.

  For best results, use an image between 400x400 pixels and 800x800 pixels - images larger than that are rarely beneficial.

  This new approach only supports the urls that the Rising Portrait feature already supports:
  * static.f-list.net (images in your character gallery)
  * freeimage.host (and iili.io)
  * redgifs.com
  * e621.net

  For more details, please see the [HQP feature page](https://frolic-chat.github.io/wiki/features/high-quality-portraits.html)

  Because this is a test, **please report your usage and experience** to the issue tracker or privately via Note/PM to the "Frolic Chat" character on f-list!

## Release 0.7.7
* Reduced memory usage
* Eicon selector overhaul. Searching is much faster. Almost *too* fast...
  There have been a few UI tweaks, but nothing major.

* Significant updates to many backend components
* Adblocker for image preview and dictionary updated

## Release 0.7.6
* Keep track of your public-room RPs better - There's a new option to match character names with your highlight words. You can find the checkbox to enable name-highlights in each tab's settings.
  * There is no global setting; this is a temporary (but fully working) solution until a larger notification revision can be made.
* The character tooltip/preview has been cleaned up.
  * On bi characters, it now shows their gender-preference, if they have one.
* Bugfix: After being bugged for literally forever, you can now view your logs from the login window, without having to log in first.
* Bugfix: The "Furs and/or Humans" preference is only used for matchmaking if species matching is indeterminate. This effectively combines them into a single score, using the most well-defined factor available.
  * Previously, a character's species could be effectively counted twice - once against Furry Preference and once against species kinks.
* Bugfix: Orientation is only used for matchmaking if gender kink matching is indeterminate.
  * Previously, a character's gender could play an overly-significant role in matchmaking.
* With the above changes, the display of matchmaking no longer shows "likes [gender/species]" multiple times.
* A short notice has been added to the smart filters settings to help you better understand the limitations of filtering.
* Bugfix: The eicon selector no longer leaks memory from over-use.
* Bugfix: The primary text box should be the correct size more frequently. This should resolve strange resizing and a scrollbar when there were no lines to scroll.
* Bugfix: On linux, the minimize button was un-minimizing the window. We've given it a stern talking-to and this should no longer be an issue.
* Bugfix: On a similar note, the chat should properly adjust to the new space when maximizing and unmaximizing the window.
* Some other mild annoyances have been fixed.

## Release 0.7.5
* Bugfix: Conflict resolution between F-Chat Rising and Frolic. No longer should they battle for control of your pinned taskbar icon.
  * **Please uninstall prior versions of Frolic and F-Chat Rising before installing this version.**
* Automatic update check
  * There is no automatic download, just a menu entry to download it for yourself. Configuration options will come once it proves to be working well.
* First stage of new desktop icons - you can enjoy them while the app is running!
* Bugfix: You can no longer save a blank memo.
  * Additionally, you can delete an accidentally blank memo by re-opening and saving it.
* Better alignment on some sidebar icons
* Lots of backend refactoring and simplification.
* Password saving got a makeover to bring the codepaths up-to-date with modern coding standards.

## Release 0.7.4
* Bugfix: Resolved missing match summary after a search due to event emitter accidentally removing character data event
* Bugfix: Resolved search ticker continuing to tick after all results were resolved, reducing responsiveness
* Bugfix: Core properly stops when you call `stop()`
* Begin the move to better debug logging
* Update to electron 22
* Bugfix: Minor editor warnings resolved
* Minor formatting changes

## Release 0.7.3
* Post-length matching was very broad in past versions, making it less-than-useful. It has been reigned in, and you can expect the following:
  * No Color/Unused if either you or they have No Preference or have their desired post-length unset.
  * Bright Green if they desire identical post-length as you desire.
  * Dim Green if their desired post-length is one-off yours.
  * Yellow if their's is two-off yours.
  * Red for everything else.

  There is an option to broaden your results again if you had no issue with prior post-length matches.
* In past versions, some errors would freeze the login screen forever. There are now explanatory error messages for the most typical cases. If you encounter a situation where you can't log in but no error message is presented to you, please file a bug report.
  * Additionally, there are warning messages at the log-in screen for situations that may indicate feature degradation - specifically, if you can't contact the Xariah eicon service. Additional warnings will be added as they come up.
* Bugfix: The 'Recon' tab in someone's profile accidentally showed duplicate entries. This is no longer the case. Some minor performance improvements have resulted from the change that fixed this.
  * Some back-end component updates were required to make all this possible.
* Minor clean-ups to the arrangement of the left sidebar in preparation for future changes. No features have been removed. Additional improvements were made for players using very large or very small font sizes.
* Bugfix: Prevent overwriting your local eicon cache with nothing when you can't connect to the eicon server. Saves downloading 20MB, infrequently.
* Bugfix: Gay TG characters will no longer match each other automatically.
* Bugfix: An invalid list of fonts was fixed. If you notice a shift in font choice, this is why; it was always supposed to be this way.

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
