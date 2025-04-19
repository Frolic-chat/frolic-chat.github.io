---
title: Coding Style
layout: default
excerpt: Examples of what the lead dev considers good code.
---
# Frolic code style enforcement
_Remember that this is a group project; you're not alone and you don't to be perfect. Asking for help or advice makes the people giving help feel good about themselves, and can give you assurity and confidence._

_This is a conceptual document and nothing in here is a hard rule. It really does not matter what you code looks like - the real test is: Does people _besides you_ understand it? If so, you're good._ 👍

Frolic does not have an enforced coding style. However, there are things you can do to make everyone's life easier. And by _everyone's life_ I mean, "_your life_ when you come back to fix something in a month and can't remember why you did what you did."

---
In no particular order:

## Indentation
Indentation's purpose is to make code blocks apparent. Reducing indentation below 4 spaces negates that feature. Therefore, indentation should be 4 spaces. Heck, try 8 spaces for all I care! 12 or 16 though - that's just satanic.

If you use 4 spaces and end up in indentation hell because of it, the code probably needs refactoring. Make it functional, then we can work on making it pretty.

Indentation for fun is also appreciated.
```
Long_Write_Task(message)
    .then(OhMyGodAnonymousFunctions)
    .catch(
        (e) => {
            //uuuuuugh
        }
    )
```

The exception is in html elements where deeply nested elements are a regularity; 2 spaces are acceptable when used with other clean coding practices.

## Put control flow statements at the beginning of the line
In a large codebase, jumping around between many different functions and files can be difficult. A lot of this struggle can be alleviated simply by making all control flow very obvious to read. Any _await_, _return_, _if_, etc. statements should appear as the very first text on their line. And yes, that includes not cuddling your _elses_.

```
Code example showing no cuddled elses
```

## Group logic into "human" named functions or variables
Properly formatting a long if-statement can be arduous and more importantly, discerning the precise intent of many factors grouped together can be diffucult far into the future. It's much nicer to use a function or boolean variable named after the user-facing scenario the if-statement is meant to confront.

This also separates the logic that gets us into a code path from the code that executes down that path, allowing someone hunting through the logic to more easily skip a part of the code they're not interested in.

```
example showing separation of if-logic from conditional code, that allows you to skip reading one or the other.
```

This also has the effect of baking in the intended user experience via the function/variable name.

## Comment blocks are beautiful.
What may be obvious _now_ will not always be, especially once you've dropped off the face of the earth and someone comes along to pick up the slack. There's already way too much undocumented code in the Frolic codebase; let's not pass this burder on to those of us who will come later. Sometimes, "those of us who will come later" is just us, two months down the road... ;)

Comments that describe the intended user experience can be very useful when fixing bugs down the line, ensuring that those bug-fixers understand why the code is the way it is, so they don't arbitrarily start chopping it up.

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

## Always use curlies for code blocks
Honestly, it doesn't matter. If-statements resulting in simple control flow really don't need curlies, but in many cases you might want to throw in a debugging statement later, so having the curlies helps.

```
// Acceptable.
if (something)
    return;
```

```
// You're just making life harder for the next idiot who wants to work on this codebase.
if (something)
    log = { time: message.time, body: message.text, file: message.channel };
```

Absolutely 100% of the time _always_ use curlies if your single-line statement uses newlines for formatting.

```
// Affront to God.
if (something)
    log = {
        time: message.time,
        body: message.text,
        file: message.channel
    };
```

## Linebreaks
Empty lines between code does not hurt anyone. Not enough linebreaks and I'll send you my optometry bill.

If you asked the question, "should I put an empty line here?" the answer is "just do it so you can stop wasting braincells thinking about it."

## Semicolons
Not using semicolons is fine, until it isn't.

Someday, you'll try to explain to someone why you always use semicolons, just like I'm trying to explain to you right now. It will be pointless, so I won't try either.

## "Pretty" Code
I'm too ugly to cast judgment.

The only thing I really care about is readability. Ugly code that's highly legible is easier to come back to than pretty code with no purpose. In all cases it's going to come down to the specifics of the flow that you're working in and the objects you have to work with.

I'm a fan of lining up like-statements:
```
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

if (chat_msg(m) && isWarn(m.text)) {
    log.debug(...);
    // Ahhhhhh, there we go!
}

if (is_warning(m)) {
    log.debug(...);
    // Best
}
```
...and I'm well aware of the people who aren't, they like to make themselves quite known :>

```
// Implies a relationship between v1 and v2
const v1 = SomeGetter(values),
      v2 = SomeGetter(other_values);

// Inappropriate.
const v1 = SomeGetter(values),
      local_store = core.cache.db;
```



## Variables Names
The less readable the name, the more local it is. We all have intellisense now, so use a human-sensible name with plenty of words other people will remember to type.

`IDIOT_SPEAK` is useful for some things, sometimes, especially when they're supposed to the focus of their block (such as dealing with system states and other non-JS related things)

`FullCaps` or `Full_Caps` for broad variables being passed around between modules and namespaces.

`camlCaseOrWhatever` is fine for class methods and such.

`all_lower_case` class methods should be used for special situations, and it's likely there's shenanigans afoot if you've gone this route.

`i` is perfect for an index that you're using right now and never again.

You should never name variables in a way that leaves someone worrying about whether all lower case variable names will collide.

`alllowercasenospaces` avoidnamesliketheseforobviousreasons.

## Nested Ifs
Nested ifs are a problem in every language. It's better to spread out the logic into a readable, sensible layout than to bunch everything up in an "efficient" way that has an if-nest 5 layers deep.

```
example showing if statement super deep, then breaking it up.
```
