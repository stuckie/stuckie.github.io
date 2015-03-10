---
title: Back to GLESGAE
author: stuckie
layout: post
permalink: /back-to-glesgae/
categories:
  - Arcade Badgers
  - GLESGAE
  - Random Gibberings
---
Well.. the past month or so has been interesting, to say the least.

I&#8217;ve had more good days than bad days recently, which has meant I&#8217;ve been able to get a couple of prototypes done &#8211; Grim&#8217;s Christmas List for LD25, and a reboot of Germies! for January&#8217;s One Game A Month, with February&#8217;s entry planned out and shall be starting on that soon.  
I&#8217;ve been keeping my hours to 15 per week &#8211; 5 hours Monday to Wednesday&#8230; and the first &#8220;full&#8221; day of work I did floored me for a couple of days! So I&#8217;m obviously not quite ready to go back into actual work as yet, but I&#8217;m getting there. And we&#8217;ll see what ATOS thinks shortly&#8230;

In the meantime, I shall be doing some One Game A Month prototypes under the Arcade Badgers banner, and reworking GLESGAE.

GLESGAE&#8217;s goals are going to be reset. The next push shall change the current LGPL license to the MPL.  
It&#8217;s also going to focus pretty heavily upon JavaScript and HTML5 support for Canvas and WebGL.  
This may sound like reinventing the wheel, or even superfluous since modern browsers have decent support now &#8211; but what about weirder platforms? Not all Mobile platforms are exactly fast enough to render the whole DOM + Canvas and get near a playable frame rate.. and the vast majority of games don&#8217;t really need much of the DOM to begin with anyway. And what about homebrew platforms like the GCW Zero, or the Pandora? Even the RasPi may have a bit of fun with a full browser and getting playable frame rates on HTML5 games.  
And yes, there are a few implementations out there &#8211; AppMobi has one, there&#8217;s Ejecta, Titanium, CocoonJS, and a slew of others&#8230; but some of them are closed source, tied to platform specifics, or pull in everything and the kitchen sink when for games we really just need Canvas, WebGL, and perhaps some networking support and other minor things.. a full DOM isn&#8217;t really necessary for us.

Some of the work has already been started &#8211; it can currently compile for Android, but doesn&#8217;t actually \*do\* anything &#8211; so the seeds have already been planted. However, some of the major restructures will be that the focus will be on GLES 2 compliance, and a total overhaul of the infamous resource system &#8211; to the point that it effectively will no longer exist. Should be fun!  
I&#8217;m also changing the current JavaScript implementation from JavaScriptCore from WebKit, to SpiderMonkey from Mozilla&#8230; which is also MPL licensed and is thus a bit nicer to deal with should I ever get around to doing commercial software.

Anyway, enough ramblings.. there&#8217;s guinea pigs to clean and feed tonight!