---
title: Engines vs Games
author: stuckie
layout: post
categories:
  - Code
  - GLESGAE
  - Random Gibberings
---
Let's have a quick moan before jumping on a train in the early hours of the morning.

I think one of the reasons why I haven't managed to get Quirks done much this month is that I've fallen into the trap of building up GLESGAE rather than the game itself - I've been building an engine rather than a game. ( Of course, the main reason is more lack of time, but this one doesn't help either! )

This is a trap I have a habit of falling into a lot, due to striving to try and get things "right" first time. That never happens! You code to what you need at that specific moment in time, and make it flexible enough to update later on, when your requirements change - part of the reason why I love component systems so much, as that's effectively what they're designed to do.

A lot of the Ludum Dare projects I've done have been built on top of my old SGZEngine ( or SGZ2D, or whatever I named it at that point in time ) which had already had a good year or so of development time pushed into it, so was pretty full fledged already. GLESGAE, on the other hand, is still in it's infancy. Getting it to do things requires actually writing the thing to do, and I think that once I get the component system and Lua bindings in, it should be easier to work with. That said, I did manage to do Thieving Fingers with it - even if it didn't get submitted in time - and that was additionally with the *broken and convoluted* Resource System, so using it is doable and especially so since I've fixed a fair amount of things since then.

But, sitting writing an engine isn't going to get the game done - and there's a constant fear of implementing engine features that aren't going to be used, which of course just wastes time.

But writing a game without an engine can make it hard to strip things out to reuse the code.

Hmm... sod it, let's go license iD Tech for Little Quirks.. I'm sure they'd find that hilarious ;)