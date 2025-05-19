This is a summary of detailed thoughts and notes about how best to address the inability to provide more highly character info without intruding on visible profile space. I submitted this to the [Horizon issues site](https://github.com/Fchat-Horizon/Horizon/issues/162) in hopes that it would garner some discussion and lead to a future implementation.

If you read this and feel like it's a cool idea, please support and discuss it there! Having a full discussion on the merits of this idea would be immensely helpful even if frolic is the only client to implement it.

---

In light of the recent push to refine matching, one issue concerns me most:

* **Profiles that are written to be read by human beings cannot be well-interpreted by a machine.**

However, this isn't a real issue. That's how they're supposed to be used. They're written so that when you or I look at them, we can discern not just the words, but the style. To dilute the flavor of one's writing so that a machine can better interpret your basball-card stats is to make a _writing collaboration forum_ less about the writing and collaboration, and more about making sure you've input your info in the most programatic and least-expressive way possible.

This is a big offense to me. People should feel free to be extravagant and creative without the need to care about how a simple machine will read them. People should be able to put whatever they want in their age or species or "looking for" and understand that the people who are *meant* to get it, *will* get it.

The profile is a work of art, and it sours me to see the matcher system given any amount of consideration when filling in free-form fields or filling up their kink list.

Except that last one. The kink list is *literally* a multi-choice list with clear categories intended to be used specifically to search for and match against. *Fill it out. **Completely.***

Yes, ***I know***, *this situation isn't as dramatic as I make it sound.* But look, I needed a hook to pull you in, because I'm about to unleash a bunch of technical bullshit that you wouldn't read otherwise.

___

There are better ways to relay complicated information specifically intended and formatted to be read by a machine.

*This proposal is only partially complete,* but given the discussion already happening around matcher make-overs, and the high potential it has to change the way people write their information, and the already oppressive atmosphere the matcher promotes, I feel it's necessary to put it out there. Additionally, all ideas need critique. So, if this reads like a scratchpad of ideas, that's because... it is. :)

### Fingering, Augmentation & Relay

I propose we use the ability to hide messages in bbcode tags to implement both short-term contact (fingering) and long-term storage (augments & relay).

The most likely candidate for this task is one of i, b, or u bbcode tags, as you can assign arbitrary text strings to them that can be parsed when requesting the profile via the API. Last month, I tested a 500+ character-long string looking something like this:

```
[i=~!@#$%^&*()_+=-0987654321`{};',./<>?:"|\123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012398765432156789012345678901234567890123456789012345609876543217890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567891234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234561234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789078900][/i]
```

And it was received and displayed fine. Meanwhile, my profile on the main page doesn't even include this tag in the rendered html, since it's converted into `<i></i>` and optimized away.

Recently, I came across someone hiding their Rising Portrait inside a tag similar. That really made my heart pang. Imagine wanting to have a fun portrait, but not wanting to spoil your finely crafted profile. They had layered the `img` tag, which was completely absent on the website but unfortunately rendered poorly in the in-app browser. Trying to stuff square brackets inside other square brackets is a disaster.

The use of hidden text can satisfy the needs of the matcher by allowing players to make their character intent clear to a robotic parser while maintaining their personal artistic integrity using their visible profile.

Let's cut straight to an example of what could be done:

```
[i=teal://k516(&p=Elf&f=Human)/t3(g3(male))/t24(&s=1&l=-1)][/i]
```

This string signifies the character is a lycanthropic transman who would prefer posts to err on the side of shorter, rather than longer - all of which is information that normal profiles cannot ever make completely clear to a machine parse, but a human would understand just fine from reading the profile.

Let's break it down:
* `[i=teal:1//` - The protocol: A name and a version number - something that can be found by both a person and a parser.
* `k516()` - Customization of kink 516 (lycanthropy)
	`&p=` primary species (usually, their actual species, or their humanoid form) - This can be coerced into (or only allow) a kink-matching species since it's exclusively for the matcher, not a human reader.
	`&f=` Whether this person wants to perceived as a furry or human for the Furry preference scale. In this case, this character should match human, not furry.
* `t3(g3())` - Customization for tag 3 (gender), gender 3 (transgender)
	`male` - Their gender identity. Potentially, there is an infinite amount of information to broadcast in gender or orientation tags. I am in favor of it. 😈
* `t24` - Customization of tag 24 (post length)
	`&s=1` - +0.5 match to all post lengths shorter than their own
	`&l=-1` - -0.5 match to all post lengths longer than their own
* `][/i]` the closing string

This could be further made shorter by removing the parentheses. *There is no necessity to the specific delimiters and combiners I used here* - this is just a demonstration to show how a variety of information styles could be joined. "Teal" was chosen because I am Not Creative and this is a **L**exicon for **A**ugmenting the matcher in a **T**ext-only **E**nvironment.

Here's a demonstration of a different formatting, implementing non-matching concepts ("relay"ing information):
```
a:1//516;Primary:Canine;Furriness:Human;;CC;name-color:#FF00FF;hq-portrait:https://i.chzbgr.com/full/10505110272/hAAA8AC15/not-part-problem-cats4yourmom-am-entire-problem;
```

This augment tag should *most likely* be anchored at the start of the profile to optimize regex speed. Here's a regex that matches the first example (if I'm not tired): `^\[i=teal:1\/\/([^\]]?)]\[\/i]`

Sadly, the js regex parser cannot match backwards, so there's no speed benefit to anchoring it at the end of a profile.

It's tempting to say we can serialize a JSON object and stuff it into a hidden tag and be done with it, but I feel that's a bad idea for a few reasons:
* Verbosity - Storing and receiving this information from the server is a privilege and should not be abused by wordy syntax.
* Legibility - This one is hard to get across without having experience working with low-tech people: A combination of the length combined with the "appearance" of being code can be disconcerting to a user deciding if they really want to paste this into their profile.
  It's weird to think this would apply to JSON and not my weird syntax, but I've helped a lot of people through technology problems and there's definitely more trepidation over something that's long and well constructed - something that looks "professional" - than a few scribbles with your kink words thrown in.
* Low Code Benefit - Even if it could be turned into an object quicker than a custom recipe, converting a string to an object isn't the heavy part of processing this concept. Integrating augments into the matcher code is where the most brainwork would need to be applied.

The necessary elements of this proposal, so we're clear:
* **Strong namespacing, including versioning.**
  This allows expansion over time, as well as fixing mistakes in the protocol and recommending the user to update an outdated augment string. Of all the components, the namespace should be the most human-readable so a user can find the string to remove or replace it manually.
  To be forward-looking, it's best to avoid branded namespacing.
* **Concise, obvious elements.**
  It's important that unaware people can recognize this isn't malicious or attempting to exfiltrate sensitive information.
  Clear and well-chosen delimiters make it easy for a user to understand the data that's being broadcast even without knowing *exactly* what's going on. Blatant delimiters also makes it easier for a machine to parse.
  Names and options should be based off their existing counterparts for consistency.
* **A UI** to assist the user in crafting one of these strings.
  Like... hands down you should just let the user select their gender identity and the species-kink they want to be matched against from a drop-down list.
* Minimize kink list overlap. It already exists; use it. Matcher augments would exist to glean explicitness that doesn't or shouldn't exist in the current profile system.

Additional augmentation I would love to provide to the matcher:
* Which species search do you want to show up in/kink do you want to match against?
* Other gender details: pronouns, perception... especially for H/Mh/S/C
* Femboys (No Further Comment.)
* Whether you like wonderwall Ironically or like For Reals.
* Post length flexibility
* Whether your Humans Only preference includes or excludes humans with animal ears.
* Any details the machine is bad at parsing currently.

Other considerations:
* The more work it takes to implement, the less likely it's going to get made.
* Documentation is key. For the users to read about it, understand it, and desire it - and for people to know what to expect and what to look out for. For example, documenting that light names on light themes will get a dark text shadow (so they won't be illegible) will stifle user complaints when they can't meme on their friends with "blank" text. It will also help future developers. :)
* These are augments/overrides, not a replacement for standard profile parsing. When a suggestion can be made using natural profile features (combination of kinks, etc), it should be done so. But if it could be done better, then it can be done in an augment. IE, trying to parse a species from "Blackscale dragon god wearing ancient knight's armor with a tiny biped samoyed lancer riding its back that can breath fire (the dog not the flying lizard)"
* Fetching (and parsing) a profile is a different call than fetching infotags. It's slower. This would be a benefit of using, say, a contact info, but the downside of that is that it's prominent on the profile, and a little strange.

---

### Relay

Besides improving the matcher, a long-term, public text storage could be used to relay generic information - such as a text color to apply to you in chat or a URL for a high-quality portrait.

Highlighting is one of many novel uses of arbitrary tagging -

* An ad could get pulled into a custom ad-browser:
```
[i=ad:The Sufferer][/i] But alas! It was only the North American release of Hybrid Theory... [i=/ad][/i]
```

* Character summary could be relevant in tooltip or character browser:
```
[i=summary][/i] Natty lizardman. No juice all game. Knows level 5 fireball with 0 points in magic 😎 [i=/summary][/i]
```

* First-message reminder or other prominent reminder to display in a blank PM window:
```
[i=first-msg][/i] I am AFK 104% of the time and not paying attention 5% of the time, +/-2%. Also I don't like you already. Delete your main.[i=/first-msg][/i]
```

---

### Fingering

Back on IRC, there was the ability to instantly query someone for basic connection information (such as their IP... The internet was a different place back then.)

Since the hidden `[i=]` trick works in chat as well (unfortunately), it can be used with immediate requests, such as asking someone in the first message if they use a custom-client and what protocols or custom features they support.

Visual:
```
You: Hi! Noticed you have "cheating" in your faves... Nice to find someone else who aimbots in COD :)
Them: send ss of bank info, this is not a scam
```

Undercover:
```
You: [i=finger:1//request][/i]Hi! Noticed you have "cheating" in your faves... Nice to find someone else who aimbots in COD :)
Them: [i=finger:1//response;teal:1;dss:2;finger:1:2;][/i]send ss of bank info, this is not a scam
```

* Safeword support! :) It could even be implemented to be sent with a custom slash command with an accompanied visible message. Receiving a message like this could tint the chat color to signal that you're in the midst of a break.
```
[i=SAFEWORD:HALT][/i](( 🛑 Woah! Hold on! ))
[i=SAFEWORD:request-status][/i](( Are we okay? ))
[i=SAFEWORD:RESUME][/i](( 💚 Okay, lets resume. ))
```

Considerations:
* Should only be allowed in PMs. Parsing from channel is just fishing to get DoSed by someone who hates fun.

---

Other Considerations:
* Do Not Ever consider a feature combating paid site benefits, such as custom titles.
* The best method for instant exchange would simply be a Custom-client Only Comms channel. Nothing quite like a good `COC { "protocol": "std1.2", "finger": "request" }`
* Async information that requires neutral storage still has no good way to implement.
  So for now, there's no way to give hidden 👍/👎 and automatically match with people who also give you a 👍.
  No way to highlight a portion of someone's profile and send it to them with a 💖 so they know what you like. Would love to be able to select 5 kinks and a paragraph and send a simple 💘 to see if I get a response. And NO i can't just ask geez do you know how cringe it is to talk to people????

Other methods that were considered but were disregarded for one reason or another:
* Steganography
* Caption text
* Eicons
* Dead contact info fields (AIM, Skype, World of Warcraft...)
* Groups
* The "User has started typing..." Indicator
* Hidden channel for Custom-client users
* Plain text in the profile



This solves two problems:
1. Encouraging profiles to become more programtic and less expressive.
2. Granting a sense of direction and explicitness to the matcher.
