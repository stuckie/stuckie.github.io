---
title: Back to GLESGAE
author: stuckie
layout: post
categories:
  - Arcade Badgers
  - GLESGAE
  - Random Gibberings
---
Well.. the past month or so has been interesting, to say the least.

I-ve had more good days than bad days recently, which has meant I-ve been able to get a couple of prototypes done ' Grim-s Christmas List for LD25, and a reboot of Germies! for January-s One Game A Month, with February-s entry planned out and shall be starting on that soon. <br />
I-ve been keeping my hours to 15 per week ' 5 hours Monday to Wednesday; and the first "full" day of work I did floored me for a couple of days! So I-m obviously not quite ready to go back into actual work as yet, but I-m getting there. And we-ll see what ATOS thinks shortly...

In the meantime, I shall be doing some One Game A Month prototypes under the Arcade Badgers banner, and reworking GLESGAE.

GLESGAE-s goals are going to be reset. The next push shall change the current LGPL license to the MPL. <br />
It-s also going to focus pretty heavily upon JavaScript and HTML5 support for Canvas and WebGL. <br />
This may sound like reinventing the wheel, or even superfluous since modern browsers have decent support now ' but what about weirder platforms? Not all Mobile platforms are exactly fast enough to render the whole DOM + Canvas and get near a playable frame rate.. and the vast majority of games don-t really need much of the DOM to begin with anyway. And what about homebrew platforms like the GCW Zero, or the Pandora? Even the RasPi may have a bit of fun with a full browser and getting playable frame rates on HTML5 games. <br />
And yes, there are a few implementations out there ' AppMobi has one, there-s Ejecta, Titanium, CocoonJS, and a slew of others&#8230; but some of them are closed source, tied to platform specifics, or pull in everything and the kitchen sink when for games we really just need Canvas, WebGL, and perhaps some networking support and other minor things.. a full DOM isn-t really necessary for us.

Some of the work has already been started ' it can currently compile for Android, but doesn-t actually \*do\* anything ' so the seeds have already been planted. However, some of the major restructures will be that the focus will be on GLES 2 compliance, and a total overhaul of the infamous resource system ' to the point that it effectively will no longer exist. Should be fun! <br />
I-m also changing the current JavaScript implementation from JavaScriptCore from WebKit, to SpiderMonkey from Mozilla&#8230; which is also MPL licensed and is thus a bit nicer to deal with should I ever get around to doing commercial software.

Anyway, enough ramblings.. there-s guinea pigs to clean and feed tonight!