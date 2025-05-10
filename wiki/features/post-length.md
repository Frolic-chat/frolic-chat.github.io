---
title: 0.7.3 "Desired Post Length" Change
layout: default
excerpt: An explanation of post-length matching
---
# Post Length
In 0.7.3 the use of your "desired post length" setting to find partners was adjusted to restrict good results to a narrower range of post lengths. This was done to address a long-running debate about recommending you play with people who cannot meet your post length desires.

There was also an inconsistency where the matcher would suggest that you're compatible with vastly higher desired post-length, but when they looked at you they would see you as incompatible.

The behavior in 0.7.3+ is:
1. If either player hasn't filled in their desired post length, or has "no preference" set, post length is not considered when determining compatibility.
1. Perfect match (bright green) for your own desired post length.
1. Good match (dim green) for the post lengths directly above and below yours.
1. Hesitant (yellow) for post lengths just outside those.
1. No (red) for any other post length.

There is an option in the settings to be more lenient, which will bring you back in line with previous behavior if you desire it.
