---
title: Orientation Matchmaking Update
layout: default
excerpt: The Rising match-maker only used character orientation for cis-gendered characters.
---
{% include development-feature-warning.md %}

# Use of "Orientation" in Matchmaking
Prior to Frolic 0.7, the Rising-based matchmaker would only use your orientation to find gender-based matches if you were male or female. We have provided some improvements to matching for other situations for which an obvious conclusion can be reached.


## Caveats
There are _many_ scenarios where the Rising-based matchmaker is incapable of providing a proper analysis of orientation vs non-binary genders. It's simply not possible for analytical tools such as computers to carry the nuance that humans do in regards to gender. _No machine is a replacement for your own eyes and critical examination._

Additionally, F-List's poorly worded genders and limited gender selection imposes additional challenges, not the least of which is that many of the available genders are considered to be outright slurs. We really wish F-List would move to an "I have: &lt;parts&gt;" and "I want: &lt;parts&gt;" system, but that's unlikely to ever happen.

Accounting for these issues is an ongoing struggle. Frolic continues to err on the side of caution when making matches, and only adds highly-typical improvements.

Additionally, matchmaking using orientation does not yet account for charaters who have the "orientation play" kink.


## Specifics
With this update, the improved orientation-matching system will account for the following scenarios, in the listed order:
1. If either character lacks a gender, orientation is not used to determine your matchability.
2. **NEW:** If either character is pansexual, asexual, or unsure, then gender is not used to determine your matchability.
3. **NEW:** If your orientation is gay and their gender is identical to yours, provide a Great match.
4. **NEW:** If your orientation is bisexual with a preference, provide a Great match for that gender.

**_The changes listed below are locked behind an experimental feature flag that must be enabled manually. Enabling these features may result in rare-but-still-possible undesirable matches. I'd love reports about results (good or bad!) with the experimental orientation matching enabled._**

5. **NEW:** If you're one of the three female-aligned genders (F, S, H) and straight orientation, match Great against males; Same for male-aligned genders (M, C, MH) and matching against females.
6. **NEW:** With a bicurious orientation, the same groupings will return a Great match for the male/female gender they're certain about, but the gender they're curious about won't be used to find matches, allowing matching based on other factors such as shared interests. (In other words, bicurious people can match against everyone, but return a green-color gender-match for their known attraction.)

**_The below scenarios are the default orientation matching criteria as inherited from F-Chat Rising._**

7. If your character isn't cisgendered and hasn't matched based on any of the above criteria, don't use gender/orientation to find partners, allowing other factors to prevail.
8. If your character _is_ cisgendered, provide highly-typical and expected matches against other cisgendered characters.
   Yes, that's right: The Rising orientation matcher only ever provided positive results for matching cisgender characters against each other.
