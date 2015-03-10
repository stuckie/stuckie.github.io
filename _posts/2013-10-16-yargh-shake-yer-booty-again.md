---
title: Yargh! Shake Yer Booty Again!
author: stuckie
layout: post
permalink: /yargh-shake-yer-booty-again/
categories:
  - Arcade Badgers
  - Code
---
This month, we&#8217;ve been working on Yargh! for the Ludum Dare October Challenge.

The past two weeks has involved me rewriting GLESGAE in C, and adding a bunch of missing functionality. It&#8217;s almost finished &#8211; I&#8217;m just fixing up a Tiled loader &#8211; and then we can start on the game code itself.  
Octopi has gone and updated a lot of the graphics from the original Yargh! already. Cleaning them up and redoing them in some cases, so it&#8217;s just me holding things up!

Currently, GLESGAE will compile and run on Android, Linux and Windows. It has (slightly puggled) OpenGL and GLES2 renderers, as well as support for SDL2 ( which is where the current work is going into. )  
&#8216;I&#8217;ve also added CMake support, to make compiling a tad easier as there&#8217;s a lot of things to turn on and off in the code now. Though I haven&#8217;t quite figured out all the options to add my super strict ANSI flags on yet, so will need to sort that out to stop me doing lazy code.

As for the game itself, we&#8217;re going to be trying to take a different route with it.  
We&#8217;re going to try and get some alpha funding for it. As such, I need to actually take some time out from the code now and then, to post updates and generally promote the game a bit. And first off, a description of what we&#8217;re up to with it would be a good start!

In keeping with the Arcade Badgers&#8217; philosophy of breaking down barriers, Yargh! is an RTS game aimed at those that perhaps can&#8217;t play traditional, often stat-heavy, RTS games.  
Borrowing a bit from The Bitmap Brothers&#8217; Z, Yargh! is stripped down to giving you one of three main tasks:

  1. Capture more islands than the other pirate leaders.
  2. Amass more gold than the other pirate leaders.
  3. Blow all the other pirate leaders out the waters ( or just have a bigger fleet, but blowing holes in enemy ships is more fun <img src="http://stuckiegamez.co.uk/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" /> )

You&#8217;ll have a time limit for each map, and the totals of your islands, gold, and pirates are tallied up at the end to define a pirate overlord.

So it&#8217;s quick, simple and just enough strategy to make you think without having lots of stats get in the way. Maths and numbers can be evil and scary for people, so by hiding that as much as possible we should open up the RTS genre to more people. That&#8217;s the theory anyway!

In keeping with the simple RTS theme, there are only two kinds of units &#8211; ships and pirates &#8211; and three types of building &#8211; docks, forts and mines.  
Capturing forts produce pirates. Capturing docks produce ships. Capturing mines produce gold. All come out in a nice steady flow, so you don&#8217;t need to micro-manage too much. Capture all forts, docks and mines on an island, and that island is tagged as yours. Simple.  
You don&#8217;t tell anything to build anything, they just do it. You don&#8217;t require resource gathering. You just capture it by sending one of your units into the building, and the job&#8217;s done.  
Pirates can capture anything, but Ships can only capture docks.  
Ships can carry Pirates from island to island.  
Ships fire cannons at Ships and Pirates.  
Pirates can fight Pirates.

And that&#8217;s about it.  
Oh, and did I mention multi-player support?  
We&#8217;ll be having that.  
And a leaderboard.  
And some achievements.

So yes, by the end of October, we&#8217;re hoping to be in a position to offer an Alpha for some funding to finish it off.  
For now, I shall leave you with Peg Leg Pete.

<div id="attachment_624" style="width: 266px" class="wp-caption aligncenter">
  <a href="http://stuckiegamez.co.uk/wp-content/uploads/2013/10/Pegleg.gif"><img class="size-full wp-image-624" alt="Peg Leg Pete dancing." src="http://stuckiegamez.co.uk/wp-content/uploads/2013/10/Pegleg.gif" width="256" height="256" /></a>
  
  <p class="wp-caption-text">
    Dance, monkey boy, dance!
  </p>
</div>