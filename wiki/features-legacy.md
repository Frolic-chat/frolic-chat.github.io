---
title: Legacy Features
layout: default
excerpt: Differences between Rising and vanilla F-Chat
---
# Legacy Features
This page outlines differences from vanilla F-Chat. This page mostly contains information related to the defunct F-Chat Rising and may not be updated with the latest changes.

## Key Differences from the original F-Chat client

1. **Profile matching** automatically compares your profile with others to determine with whom you are compatible.
1. **Automatic ad posting** repeatedly posts and rotates ads on selected channels.
1. **Link previews** popup shows a preview of an image / video when you hover your mouse over a link.
1. **Caching** speeds up profile loads and other actions.
1. **Smart filters** let you choose what kind of ads and posts you see in the chat.

## Features
*   Channel Conversations
    *    Highlight ads from characters most interesting to you
    *    Hide clearly unmatched ads
*   Ad Auto-Posting
    *    Manage channel ad settings via "Tab Settings"
    *    Automatically re-post ads every 11-18 minutes (randomized) for up to 180 minutes
    *    Rotate multiple ads on a single channel by entering multiple ads in "Ad Settings"
    *    Channel owners can set a minimum time between ads by adding `[ads: 30min]` to the channel description 
*   Ad Ratings
    *    LFP ads are automatically rated (great/good/maybe/no) and matched against your profile
*   Private Conversations
    *    View a characters' recent ads
    *    Quick prof  
*   Link Previews
    *    Hover cursor over any `[url]` to see a preview of it
    *    Hover cursor over any character name to see a preview of the character
    *    Middle click any `[url]` to turn the preview into a sticky / interactive mode
    *    Link preview has an ad-blocker to minimize page load times and protect against unfriendly scripts 
    *    Use alt/option key + mouse click to pin the link preview
*   Profile
    *    Kinks are auto-compared when viewing character profile
    *    Custom kink explanations can be expanded inline
    *    Custom kinks are highlighted
    *    Gender, anthro/human preference, age, sexual preference, and sub/dom preference are highlighted if compatible or incompatible
    *    Guestbook, friend, and group counts are visible on tab titles
    *    Character images are expanded inline
    *    Cleaner presentation for the side bar details (age, etc.), sorted in most relevant order
    *    Less informative side bar details (views, contact) are separated and shown in a less prominent way
    *    Cleaner guestbook view
    *    Profiles, images, guestbook posts, and groups are cached for faster view
    *    Character view tabs (overview, images, etc.) stick to the top 
    *    Show/hide current profile with Ctrl+P or Command+P
    *    Navigate back and forward in character profile view history
    *    Profile Analyzer guides you to adjust your profile to maximize matches
*   Character Search
    *    Search results are sorted based on match scores
    *    Best matching profiles get a 'unicorn' tag
    *    Display match score in search results
    *    Current search filters are listed in the search dialog
    *    Search filters can be reset
    *    Search results can be filtered by species
    *    Search results can be filtered by body type
    *    Last 15 searches are stored and can be accessed from the 'Character search' dialog
*   Smart Filters
    *    Filter out ads, channel posts, and PMs from characters based on filters such as age or kink preferences 
    *    Auto-respond to PMs with a 'no thanks' when character profile matches with your smart filters
*   Character Status Message
    *    Last 10 status messages are stored and can be accessed from the 'Set status' dialog
*   General
    *    Character profiles, guestbooks, friend lists, and image lists are cached for faster access
    *    Conversation dialog can be opened by typing in a character name
    *    Message search matches character names
    *    PM list shows characters' online status as a colored icon
    *    Use `Ctrl+Tab`, `Ctrl+Shift+Tab`, `Ctrl+PgDown`, and `Ctrl+PgUp` to switch between character tabs
    *    Show number of unread notes and messages in the bottom right corner
    *    Colorblind mode
    *    Option to disable Windows high contrast mode
    *    Right click any word and select 'Look up...' to see its dictionary definition
*   Technical Details for Nerds
    *    Upgraded to Electron 17.x
    *    Replaced `node-spellchecker` with the built-in spellchecker that ships with Electron 8+
    *    Multi-language support for spell checking (Windows only – language is autodetected on MacOS) 
