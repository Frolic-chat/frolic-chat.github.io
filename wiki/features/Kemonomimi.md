---
title: Kemonomimi matching
layout: default
excerpt: How to ensure you're perceived as kemonomimi
---
# 0.5.0 The Great Catgirl Remix
This update adds the necessary architecture to support kemonomimi in Furry Pairing matching.

<small>A _kemonomimi_ is a humanoid character with animal ears, and possibly a tail or other obvious animal feature (like a shell for a turtle-person). The matchmaker figures out if your character is a kemonomimi by looking for an obvious kemonomimi species in your "species" field or by checking that you have an animal species and a "human" body type. If your furry character is incorrectly being detected as a kemonomimi instead of an anthro, change your body type to "anthro".</small>

Catgirls are frequently considered human-ish by furries and furry by humans. The issue is most obvious in the "Furry preference" selector which only lets you select humans or furries (or both) as a prefered partner.

Does this mean cute beetleboys should only be marked compatible with players who put "furries and/or humans" as their preference? We have a better solution: Let every doggirl herself decide whether she should be read as human or furry. By default, kemonomimi will be considered furry. However, by choosing certain options on their profile the character matcher will consider them as human.

A bunboy can set his perception preference in one of the following ways:
1. Set Partner Preference to "No humans" or "Prefer humans, furries ok".
2. Add Humans in your Favorite or Yes kinks, and leave Anthros out of them.
3. Add Anthros in your Maybe or No kinks, and leave Humans out of them.

In many cases, a pairing preference simply won't show up as part of the matching criteria. This is done to give favor to other factors with definitive results — such as your kink overlap and post length.

*Remember:* It is not possible for an automated machine to make decisions for you, but hopefully this change will make your partner selection easier by showing you potential partners with caveats.

<small>While it would certainly be better to just have a checkbox, the chat client cannot send arbitrary data across the F-List network, therefore there'd be no way for other chatters to detect what you've set. Therefore, some manner of transferable information needs to be used. This is the best we have for now.</small>
