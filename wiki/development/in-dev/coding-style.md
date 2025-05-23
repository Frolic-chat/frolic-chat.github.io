---
title: Coding Style
layout: default
excerpt: Examples of what the lead dev considers good code.
---
# The Great Code Style Debate
When some people get old and curmudgeony, they get even more bitter and set in their ways. Now that I'm old and curmudgeony, I've stopped caring about opinion-based argument.

_Remember that this is a group project; you're not alone and you don't have to be perfect. Asking for help or advice makes the people giving help feel good about themselves, and can give you assurity and confidence._

## The Grand Rules of Code Quality
1. **"Quality" means "maintainability"**: There is no purpose in writing clean code except to make it easy for people to read it.
2. All styles will make sense to someone, and won't make sense to someone else.
3. Because code is read with human eyes (for now), empty space is not necessarily wasted space.
4. Humans perceive patterns - using human patterns can allow another contributor to _understand_ without having to _read_.
5. If a particular function is complex, it can look complex. If it's simple, it should look simple.

---
_This is a conceptual document and nothing in here is a hard rule._ **Code style is entirely about maintainability.** _It really does not matter what your code **looks** like - the real test is: Do people _besides you_ understand it? If so, you're good._ 👍

## Code Style Enforcement
Frolic does not have an enforced coding style. However, there are things you can do to make everyone's life easier. And by _everyone's life_ I mean, "_your life_ when you come back to fix something in a month and can't remember why you did what you did."

---
In no particular order, here are some demonstrations of code that might be good or bad.

## Hiding Things
Code in a way that makes it easy to find the boundaries between parts.
```ts
// Bad: argument_a and argument_b are difficult to find.
MyFunction(argument_a, argument_b, (option_a, option_b, option_c) => {
    // ...
})

// Better. Calling MyFunction() was going to take multiple lines anyways.
MyFunction(
    argument_a,
    argument_b,
    (option_a, option_b, option_c) => {
        // ...
    }
)

// I wouldn't even turn this down, but I *will* facepalm. And laugh at you.
MyFunction(argument_a, argument_b
    (option_a, option_b, option_c) => {
        // ...
    }
)

// Also highly readable, but you might violate some personal line-length standard:
MyFunction( argument_a,
            argument_b,
            (option_a, option_b, option_c) => {
                // ...
            }
)

// Bad: No additional clarity gained by spacing a simple function out like this.
No_Complex_Args.Function(
    simple_arg_a,
    simple_arg_b,
    simple_arg_c
)
```

## Indentation
Indentation's purpose is to make code blocks apparent. Reducing indentation below 4 spaces negates that feature. Therefore, indentation should be 4 spaces. Heck, try 8 spaces for all I care! 12 or 16 though... now you're speaking in tongues.

If you use 4 spaces and end up in indentation hell because of it, _that's good_ because it makes it clear to you the code probably needs refactoring. But first settle on making it functional, then we can work on making it pretty.

I can also appreciate indentation in fun ways - Again: as long as it makes the code _easier_ to read, not _harder_.
```ts
Long_Write_Task(message)
    .then(NamedFunctionsAreSoNice)
    .catch(
        (e) => {
            // 4 spaces are only a problem because you're inlining the function
        }
    )

// The improvement here is nebulous, but I won't complain.
Long_Write_Task(message)
    .then(Readably_Named_Function)
    .catch((e) => {
        // ...
    })
```

The exception to 4-spaces is in html elements where deep nests are a regularity; 2 spaces are acceptable when used with other coding practices that promote clarity.

## Put control flow statements at the beginning of the line
In a large application codebase, jumping between many different functions and files as you bughunt can be stressful. A lot of this struggle can be alleviated simply by making control flow very obvious to read. Any _await_, _return_, _if_, etc. statements should appear as the very first text on their line. And yes, that includes not cuddling your _elses_.

```ts
// Unpleasant
// Why do js developers simultaneously complain about line length and also do this?
if (!player.name) await player.refetchData();
if (!player.name) return '<Unknown>';


// Absolutely insane.
let f = 44,
    i =  0; if (f > i) await Build_Index_Pool(i);


// But this is fine.
let f = 44,
    i =  0;

if (f > i)
    await Build_Index_Pool(i);


// Simultaneously achieves the mythical infinitely short lines and is somehow still highly readability.
if (!player.name)
    await player.refetchData();

if (!player.name)
    return '<Unknown>';
```

## Single vs Double Quotes
Recently I went through a list of strings and hardly noticed that one of them was using standard quotes instead of single quotes. Prefer single quotes for simple strings and double quotes if you need to include a single quote in the string, but I'm unlikely to notice if you "screw it up". It's such a minor point, I don't understand how people make a big deal of it.

## Group logic into "human" named functions or variables
Properly formatting a long if-statement can be arduous and more importantly, discerning the precise intent of many factors grouped together can be diffucult far into the future. It's much nicer to use a function or boolean variable named after the user-facing scenario the if-statement is meant to confront.

This also separates the logic that gets us into a code path from the code that executes down that path, allowing someone hunting through the logic to more easily skip a part of the code they're not interested in.

```ts
// Necessarily complex
if (
    (player1.Life < Defaults.Life.Min && IsAnyBuffActive(player1, ...core.buffs.HasTag(PlayerState.Invincibility)))
    || ((player1.Life - player1.pendingDamage) < Defaults.Life.Min)
) {
    // show warning
}

// can still be simplified
is_alive_beyond_death(c: Player): boolean {
    return c.Life < Defaults.Life.Min &&
            IsAnyBuffActive(c, ...core.buffs.HasTag(PlayerState.Invincibility));
}

will_be_dead_soon(c: player): boolean {
    return (c.Life - c.pendingDamage) < Defaults.Life.Min;
}

if (is_alive_beyond_death(player1) || will_be_dead_soon(player1) {
    // ... show warning
}
```

This also has the effect of baking in the intended user experience via the function/variable name.

## Comment blocks are beautiful.
What may be obvious _now_ will not always be, especially once you've dropped off the face of the earth and someone comes along to pick up the slack. There's already way too much undocumented code in the Frolic codebase; let's not pass this burder on to those of us who will come later. Sometimes, "those of us who will come later" is just us, two months down the road... ;)

Comments that explain why an unusual method was chosen are useful.

Comments that explain how an outside source of information helped us decide something are useful.

Comments that describe the intended user experience can be very useful when fixing bugs down the line, but can get very wordy very fast.

```ts
/**
 * Color regexes are available in CoreBBCodeParser in bbcode/core.ts.
 * In fact, there's probably a way to reuse those.
 */
const validColors = ['red', 'blue', 'white', 'yellow', 'pink', 'gray', 'green', 'orange', 'purple', 'black', 'brown', 'cyan'];
const invalid: string[] = [];
// ...
```

## Line length
_A line is never too long, nor is it too short, it is precisely the length it is meant to be._

The last time I used a text editor that didn't offer line wrapping was over 30 years ago.

* If a long list of enumerated strings is bothering you, instead of breaking up the line by length you should consder why it's a single list to begin with.
   There may be logical groups you can break it up into, and label with comments.
   Or break it up into separate lists altogether, label those lists with descriptive names and then concatenate them. Byd oing this, the groups may be addressable on their own if needs be.

* If a function call's parameters are bothering you - why? It doesn't matter how many lines you break them up into, I'm only going to read the name to know what it does. The parameters are for the code, it's the function name that exists for you & I.
   This is _especially_ true if you're passing an anonymous object to a function call. I'm _definitely_ not reading that, though when writing it you'll definitely do so as multiple lines.

For _short lines_, I find it quite unpleasant to read lines that are only punctuation, except when they are pointed and deliberately so - but typescript has very little of that. My biggest dispute with common practice is the ugly `) {` that ends if-logic and start

## Block length
Squishing code together makes a block unreadable, but so does unecessarily stretching it out.

## Use curlies for complex code blocks
Honestly, it doesn't matter. If-statements resulting in simple control flow really don't need curlies, but in many cases you might want to throw in a debugging statement later, so having the curlies present helps.

```ts
// Acceptable.
if (something)
    log = MyChannel.createLog();

// You're just making life harder for the next idiot who wants to work on this codebase.
if (something)
    log.push({ time: message.time, body: message.text, file: message.channel });

// Any time you stretch out a statement over multiple lines, add the curlies.
// It's all about the readability, not the technicality.
if (something) {
    log.push({
        time: message.time,
        body: message.text,
        file: message.channel,
    })
}

// Affront to God.
if (something)
    log.push({
        time: message.time,
        body: message.text,
        file: message.channel
    });
```

## Linebreaks
Empty lines between code does not hurt anyone. Not enough linebreaks and I'll send you my optometry bill.

If you asked the question, "should I put an empty line here?" the answer is "just do it so you can stop wasting braincells thinking about it."

## Semicolons
Not using semicolons is fine, until it isn't.

Someday, you'll try to explain to someone why you always use semicolons, just like I'm trying to explain to you right now. It will be pointless, so I won't try either.

## "Pretty" Code
I'm too ugly to cast judgment.

The only thing I really care about is that I can read it. Ugly code that's highly legible is easier to come back to than pretty code with no purpose. In all cases it's going to come down to the specifics of the flow that you're working in and the objects you have to work with.

## Statements of Similar Purpose
I'm a fan of lining up like-statements to demonstrate their association:
```ts
if (m.type === MessageType.Message
 || m.type === MessageType.Ad
 && isWarn(m.text)
) {
    log.debug(...);
    // But this creates the freaky ) { setup :<
}

if (m.type === MessageType.Message
 || m.type === MessageType.Ad
 && isWarn(m.text)) {
    log.debug(...);
    // Somehow, we made it even worse.
}

if (standard_msg(m) && isWarn(m.text)) {
    log.debug(...);
    // Ahhhhhh, there we go!
}

if (is_warning(m)) {
    log.debug(...);
    // Best, it confirms that it's all part of the same conceptual check.
}
```
...and I'm well aware of the people who aren't, they like to make themselves quite known :>

```ts
// Implies a relationship between v1 and v2
const contestant_a = SomeGetter(values),
      contestant_b = SomeGetter(other_values);

// Inappropriate; you're making it appear like there's a relationship when there is none.
const contestant_a = SomeGetter(values),
      context = core.cache.db;
```

## Nested Ifs
Nested ifs are a problem in every language. It's better to spread out the logic into a readable, sensible layout than to bunch everything up in an "efficient" way that has an if-nest 5 layers deep.

```ts
// I don't know if I really need to show an example.
```

## Complexity
You will never look simple to check 6 million different variables at once. That's because it's not. However, you can make simple code look simple, so that when you encounter complex code, you recognize it's complexity.

```ts
// Apparent complexity on first glance due to line length
return (invalid.length > 0) ? invalid.join(', ') : null;

// But it's actually just a basic boolean check.
// Each possible return is easy to find.
return (invalid.length > 0)
    ? invalid.join(', ')
    : null;

```
