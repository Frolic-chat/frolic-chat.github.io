---
title: Species Matching Details
layout: default
excerpt: Details about how species matching is done
---
# Species Matching in Frolic
## Abstract
F-List allows players to assign species to their kinks list, showing a Favorite/Yes/Maybe/No preference towards a given species. However, F-List does not allow any way to match those species preferences to a player's manually-entered species phrase. This means players have to sift through other players' kinks list just to figure out if their species is acceptable to that player. A lot of frustration can arise from finding a character and deciding you're a good match, only to get to the very bottom of their kinks list only to find they've put your character's species is a firm "No".

Frolic continues to use F-Chat Rising's matchmaker for species matching. The Rising matchmaker uses a list of creatures that players enter on their profile, and pairs them to a generic creature name. For example, most creatures that start with "Were" are collectively grouped under "Lycanthrope".

Species are added to the list of detected species manually by Frolic developers. The full mapping of species is [quite extensive](https://github.com/Frolic-chat/Frolic/blob/master/learn/matcher-types.ts#L524).

Being able to determine a common species for a variety of phrases is important to the matchmaker, as it attempts to solve the problem of matching a free-form field to a predefined list of kinks.

## How It Works
Here's how a players' species phrase is paired to a species kink:

1. If you left your species phrase empty, Frolic will try to detect if you're furry-friendly.
   If your profile has specific anti-furriness, your species will be assigned human as a guess.

   <small>There are a surprising amount of players who don't fill in their species under the assumption that it's irrelevant because they're not furries. This step is an attempt to properly support these people without interfering with more firm species prediction.</small>

   If your species is empty and there are no clear signs of being anti-furry, your species remains empty and won't display in the tooltip or be used for matchmaking.

2. Your species is compared to two maps: The map of _likely human_ phrases, and the map of firm species phrases.

   The program maintains manually compiled maps of _species_ (from the kinks list) to species _phrases_ (that players can enter on their profile). The maps are iterated through, checking if your species phrase matches any of the mapped phrases. If a match is found for your phrase, the species associated with that phrase is determined to be your species.

   * Your species phrase is converted to lowercase and spaces are trimmed from the front and back.

   * The mapped phrases are blocked from being part of a composite word, to avoid accidentally detecting that your phrase "catgirl" contains the mapped phrase "cat".

   * Plurals are matched.

     This way "a horde of cats" and "a cat" will both be detected to contain "cat". <small>Complex plurals such as _elf_ to _elves_ are not checked, on account of it being difficult. "Three elves standing on each other" isn't a very common species, anyway.</small>

   * The longest possible match is used.

      Your species phrase "were cat" would initially match ".*cat". However, "were cat" would _then_ be matched as "were[- ]?cat". Because "were[- ]?cat" is longer, it would take precedence to match.

      <small>This could be a reason your species phrase doesn't seem to be pairing up to the species you expect. In this case, please open a [new issue](https://github.com/Frolic-chat/Frolic/issues) on our tracker so we can confront this.</small>

3. If your species _fails to match anything_, it's passed on to the tooltip verbatim but won't be used for species matching.

   If your log level is set to "debug" or "silly", unknown species will appear in your application log file. <small>It's not recommended to set your log level this high unless you're helping develop Frolic.</small>

4. If your species matches a likely human phrase but no definitive species, you're determined to be human.

   This step trips up a lot of unique species phrases and is likely where things have gone wrong if your furry character is being detected as human. You can look over the [likelyHuman phrase map](https://github.com/Frolic-chat/Frolic/blob/master/learn/matcher-types.ts#L497) to determine how you got matched, then report a bug on the [issue tracker](https://github.com/Frolic-chat/Frolic/issues) if you believe something should be adjusted.

5. If your species phrase matches a mapped species, you're determined to be that species.

6. Your determined species is automatically mapped to its matching kink, if there is one. That kink is looked at on other characters' profiles to check if they're compatible with your character! 🌼

## Best Results
First, use whatever species phrase you like and check your own tooltip to see which grouping you get put in. If it's wildly inaccurate, report it on the [issue tracker](https://github.com/Frolic-chat/Frolic/issues). (For example, if you're an American Bombay cat and the tooltip says you're a canine.)

If you aren't put in the right kink category, confront any obvious signs - such as double-checking your spelling or using more common terminology for the species.

Since the species phrase will have "word boundaries" added to it, "dogcat" may not match you as either "cat" or "dog". Consider introducing a space, comma, slash, or other non-word character if you want to match one or the other.

Additionally, if you're multi-lingual, consider using an english species name if you're looking to get matched with english-speaking players.

If your profile represents an abstract concept, try to use a common phrase that represents that concept. Frolic currently matches "hub", "room", and so on as hub profiles, allowing people to easily move past if they're not interested in that. "Shapeshifter", "varies", "many" are also valid species that Frolic will relay to potential partners.

## Caveats
_Any "understanding" a computer application has must be programmed into it. A computer will never "know" something unless a human being explicity programs the complicated logic into it. Keep in mind this limitation when thinking about how species matching works._

* Not all _possible_ species are added. It does not make sense to add species no one plays, since they have to be manually added and every new species makes Frolic run ever-so-slightly slower. For example, it would be pointless to add every single pokémon to the list when only a handful of them are actually played.

* Non-english language species are rarely added, as we do not have dedicated non-english-speaking contributors to evaluate the validity of various phrases.

* Unique spelling or misspelled words will fail to get you categorized. Only the most common misspellings are accounted for in cases where they are made frequently.

* Using special unicode characters to deliberately obfuscate the species (such as full-width characters or mathematics letters) will always thwart species matching, and those people don't seem that concerned with it, so we don't bother.

* Human consideration must be applied, no matter how flawed. There is no good way to know the root species of any specific creature name without research and consideration.

   For example, mermaids are not currently considered lamia/naga - they're considered exotic species. This is due to two factors: Lamia as a concept have an inherent association to the mythical, while mermaids continue to exist in modern day pop culture; and in practice, players who type in "mermaid" are more likely to be have a character that meets the pop culture definition. In essence... mermaid aren't lamia for no greater reason than "we thought about it for a while, and they aren't".

   The same holds true for "golem" which has many definitions, the most traditional of which could classify its species as either robot, humanoid, or monster. In this case, there aren't enough golem characters on F-List to warrant this much consideration, so golems are placed under exotic species.

Despite all the flaws of having to associate manual-entry species with a limited list of kinks, we lack a better method to provide this feature, so Frolic will continue to use this approach. You are invited to propose a better solution, just keep in mind the amount of effort it would take to implement, and the amount of other very cool things we would rather be working on.
