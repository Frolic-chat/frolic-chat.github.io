---
title: Decision Making in Design
layout: default
excerpt: How are Frolic's design decisions made?
---
# Personal Decisions

## Abstract
There are many choices that simply can't be decided in a way that satisfies everyone. If you offered a single meal to every person on the planet, you would find _someone_ who wouldn't care for it.

In Frolic, there are many places where these decisions have to be made.

## Innocuous Decisions
Thankfully, many places where a choice can be made between two almost-equal choices. For example: `Settings` vs `Options` - it really _doesn't matter_, they both convey approximately the same idea and both have been used for the same purpose in many other applications without conflict.

For innocuous decisions:
1. Choose the one you think works best;
2. Listen if someone has a point to prefer the other;
3. Recognize that it really doesn't matter in the end.

## Decisions Needing Consideration
Some are a little less clear, but still work as long as you try your best. For an exmple, lets take the situation where a new feature needs to be described to a user.

The actual description of the feature is long and detailed. It is all relevant to users wanting to make the best use of the feature, but most of that information isn't necessary to start playing around with this new toy.

Therefore, we can satisfy both uses by including a rough outline of the feature in-app, and providing a link to more detailed information at the end of the explanation. However, some people will not be happy they have to go to another page to view details they consider relevant, and they may also not appreciate certain facets of the feature being buried in a long, descriptive document instead of being in the short, easy-to-read in-app blurb.

_How much_ and _which_ information should be included in-app can never be decided on in a way that satisfies everyone, but we can consider the ways people will interact and reach a point where the decisions becomes innocuous:

1. Consider the amount of friction you're introducing - in this case, increasing the amount of info provided in-app makes it seem difficult to parse, while providing a simple button to open the full document is very little work to access extra information.
2. Consider alternatives: Instead of opening a webpage, you could expand the page downwards with further information, or allow the link to open the full documentation in-app.

But at point two, we're already at "Settings vs Options" levels of innocuous: asking someone to open an in-app webpage vs an in-browser webpage... there's not enough difference for it to truly matter.

## Decisions with Consequences
Every application is biased by necessity. It's not just the language of its words, but the language of its _design goals_, _feature set_, and the _UI_ that makes it all accessible.

### Features
Applications let you _do_ things, and some apps make their statement in the features they offer. For example, a truly private chat application wouldn't offer a Report feature, because that would offer a direct violation of the privacy it's supposed to endorse.

The mere act of _offering_ to let you report people you're privately chatting with changes the statement the application is making, and by extension changes the way you think about it and use it. The knowledge that people can be reported (hopefully) makes them behave better, and also discourages them using the chat for any activities they wanted to be private.

Deciding which features to offer is not simply a matter of "which features are _good_" but "which features build the experience I want to offer".

### UI
The placement of UI elements on a canvas can be done in an infinite number of ways. There is no correct way to design a UI and debates about whether a UI is designed correctly or not tend to reflect the internal biases of the debaters. What makes a "good" UI is nebulous in even the most specific scenario.

If you try to "do your best" to try to find some commonly acceptable arrangement, you'll end up with UI that looks like it was designed in the early 2000s. Or Libreoffice. In this case, there's a better way to do things: Design towards your application's _purpose_.

By forcing your UI design to forward the goals of your app, you make it clear on the face what you're trying to accomplish. Users who align with your purpose will be more attracted to your app and feel at home using it, while users who don't will feel immediately put off and know this isn't the app for them.

A user's attitude will be shifted by the way a UI is made and the way a user is escorted through it. For example, having lots of nested menus will lead a user to feeling directionless and lost. They'll lose track of what they were trying to find and will give up, feeling frustrated. Any app that actually _wants_ the user to change their settings will make it easy to locate one's desired change.

You should be careful, though: Trying to force together an interface that's a radical departure from the norm will put off everyone, everywhere.
