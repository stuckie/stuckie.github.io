---
title: Labyrinth
author: stuckie
layout: page
---
<div style="text-align:center; font-size:24px; font-weight:bold; text-decoration:underline;">
  Sonic Death Monkey<br /> <img src="/gamez/labyrinth/SDM.png" alt="Sonic Death Monkey" />
</div>



<div style="text-align:center; font-size:18px; font-style:italic; text-decoration:underline;">
  Labyrinth
</div>



As part of Sonic Death Monkey, I was responsible for the engine, tool-chain and pulling everyone&#8217;s code changes together.  
In essence, I was the Lead Programmer, in a team of five programmers for our Prototype Game Development module &#8211; otherwise known as The Third Year Group Project.

We had settled on doing a Diablo-like clone, and the tasks had been split up so that there was a dedicated AI programmer, Physics programmer, Interface and GUI Programmer, Camera programmer and Engine programmer &#8230; with the notion of us all doing Gameplay programming where needed.  
Unfortunately, the scale of the task at hand caught us completely off guard and we spent our time focused on our respective roles, rather than paying any attention to the Gameplay itself.  
It did not help matters that the engine was using programming concepts that were somewhat strange to the others in the team, which gave them a steep learning curve in implementing what they had to do in the first place.  
Secondly, when I did receive updates to pull together, each programmer tended to stick to a specific revision they were using, rather than the updated revisions I had been sending back almost every week.. this meant that some changes were reverted and bugs crept in and out on a regular basis. We needed source control, but we hadn&#8217;t taken the time to set it up to begin with, and by the time we realised we really needed it, it was too late.

Although the project didn&#8217;t meet our expectations, we still gained a lot of experience from it.  
We managed to work together towards the end to produce something that actually did work, although was very basic. We also realised that not using source control was a very bad idea, and that trying to keep up with the &#8220;bleeding edge&#8221; of our graphics engine, was also a very bad idea and we should have stuck with one specific version and not touched it afterwards.  
These are all lessons that while seem common sense now, we didn&#8217;t quite realise at the time, and has made us better programmers for it. 



## Downloads

Firstly, I apologise for the sheer size of these downloads &#8211; they&#8217;re both 20+MB!  
[Labyrinth Win32 Binary ( 25mb 7z )][1]  
[Labyrinth Source ( 22mb 7z )][2]  
[Labyrinth Design Doc ( 1.1mb Word Doc )][3]

The design doc is 68 pages long and is a conversion of the original design wiki we used.  
We managed to make this 68 pages by mangling the margins somewhat, as the original was closer to 100 pages with &#8220;standard&#8221; margins!  
The Doc is also quite in-depth and details a lot of things that the &#8220;full game&#8221; would have had. We were just creating a prototype of all this, but our design doc had to be on the full game, rather than the prototype.  
Should be an interesting read anyway!

If you&#8217;re going to attempt to use the source, you&#8217;ll also need the Binary too for the &#8220;media&#8221; folder. Unfortunately, the &#8220;media&#8221; folder was never properly cleaned out, so all the Ogre gumf is still in there! Hence the huge size!  
Vista users also won&#8217;t be able to see much, as we only have the OpenGL driver for Ogre in here&#8230; which Vista seems to hate and give an insanely low draw distance.  
It works fine in XP, however.  
Music is also disabled, but you can listen to it manually either from the media folder, or by downloading the MP3s from this site.  
Apologies for no screen shots, it turns out the way we coded the input system really doesn&#8217;t like losing focus, and will crash if you attempt to alt-tab or anything gains greater priority! MSN Status Popups for instance..

## Resources

We used a CVS version of OGRE. Not the wisest of moves as they were in the process of going from 1.2 to 1.4 ( so in Ogre terms, we were using a 1.3 release <img src="http://stuckiegamez.co.uk/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" /> Seeing as they&#8217;re now up at 1.6 as of time of writing, it was a while ago! )  
We also used a very much hacked about version of the SGameZ Engine.. this showed me that I really needed to do another engine, which is how the Honours Project started.  
I also did the music, of which you can find over on the music project page.  
Graphics were done either by Niall Broadley or were stock Ogre models.

## Project Status

I received an A for this, so I&#8217;m happy about that!  
I doubt I will ever go near this again, to be honest. I like the idea of doing a Diablo clone, however.. so I may revisit the idea but Labyrinth is done and dusted as far as it&#8217;s concerned.

 [1]: /gamez/labyrinth/LabyrinthBIN.7z
 [2]: /gamez/labyrinth/LabyrinthSRC.7z
 [3]: /gamez/labyrinth/SONIC_DEATH_MONKEY.doc