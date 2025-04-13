---
title: Member List Sorting
layout: default
excerpt: Sorting the member list by gender accounts for your character's preferences.
---
{% include development-feature-warning.md %}

# Member List Sorting
Did you know you can sort the member list of a channel by clicking the dual-triangles next to the member count? I didn't either!

<div class="centered" markdown="1">
![Dual Triangles that Sort](member-sorting/250411-154812%20Selection.webp)
</div>


## Improved Functionality
Prior to Frolic 0.7, member list sorting used a list of genders with a fixed order. Frolic improves this to account for the gender preferences of your character. It draws upon your character's kinks and orientation to re-sort the list with your prefered genders at the top.

Additionally, the icon has been changed to one that makes more sense for its functionality. Hopefully, more people will realize you can sort the member list.


## Caveats
Sorting when two genders are equally desired (such as having both "males" and "females" in your favorites) is determined by localized alphabetic ordering of the American English gender names. The english sorting for a pansexual with no gender kinks is: `C > F > H > M > Mh > None > S > T`

Your character's gender preferences are only detected when you login. If you update your character's preferences and want to see a new sort-order, log out and back in.
