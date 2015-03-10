---
title: Engines vs Games
author: stuckie
layout: post
permalink: /engines-vs-games/
categories:
  - Code
  - GLESGAE
  - Random Gibberings
---
Let&#8217;s have a quick moan before jumping on a train in the early hours of the morning.

I think one of the reasons why I haven&#8217;t managed to get Quirks done much this month is that I&#8217;ve fallen into the trap of building up GLESGAE rather than the game itself &#8211; I&#8217;ve been building an engine rather than a game. ( Of course, the main reason is more lack of time, but this one doesn&#8217;t help either&#8230; )

This is a trap I have a habit of falling into a lot, due to striving to try and get things &#8220;right&#8221; first time. That never happens! You code to what you need at that specific moment in time, and make it flexible enough to update later on, when your requirements change &#8211; part of the reason why I love component systems so much, as that&#8217;s effectively what they&#8217;re designed to do.

A lot of the Ludum Dare projects I&#8217;ve done have been built on top of my old SGZEngine ( or SGZ2D, or whatever I named it at that point in time ) which had already had a good year or so of development time pushed into it, so was pretty full fledged already. GLESGAE, on the other hand, is still in it&#8217;s infancy. Getting it to do things requires actually writing the thing to do, and I think that once I get the component system and Lua bindings in, it should be easier to work with. That said, I did manage to do Thieving Fingers with it &#8211; even if it didn&#8217;t get submitted in time &#8211; and that was additionally with the &#8220;broken and convoluted&#8221; Resource System, so using it is doable and especially so since I&#8217;ve fixed a fair amount of things since then.

But, sitting writing an engine isn&#8217;t going to get the game done&#8230; and there&#8217;s a constant fear of implementing engine features that aren&#8217;t going to be used, which of course just wastes time.

But writing a game without an engine can make it hard to strip things out to reuse the code&#8230;

Hmm&#8230; sod it, let&#8217;s go license iD Tech for Little Quirks.. I&#8217;m sure they&#8217;d find that hilarious <img src="http://stuckiegamez.co.uk/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" />