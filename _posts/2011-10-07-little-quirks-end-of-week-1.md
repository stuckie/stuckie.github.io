---
title: 'Little Quirks &#8211; End of Week 1'
author: stuckie
layout: post
permalink: /little-quirks-end-of-week-1/
categories:
  - GLESGAE
  - Ludum Dare
  - October Challenge 2011
  - Random Gibberings
---
Well, it&#8217;s Friday, so what have I managed to get done this week?

Sadly, not much&#8230; I still haven&#8217;t started on the actual game logic, nor have I even finished the Renderer changes&#8230;  
It&#8217;s not that the Renderer changes have been difficult &#8211; all the rendering logic was there, it just needed moved about a bit, it&#8217;s that things have just been too stressful to concentrate much.  
The plus side is I should have the Renderer fixed up and running again &#8220;soon&#8221; &#8230; and I&#8217;ve also done some fiddlings to Resource so it can act as a shared_ptr in it&#8217;s own right, as well as allow it to recast itself into other types where necessary ( for example, passing a RenderWindow into the X11 Event System and recasting it to a X11RenderWindow while keeping it within a Resource object so it dies properly when there are no more references to it. )

None of the engine is thread-safe in the slightest at the moment, though I&#8217;m not too bothered about that for now.. there are a few sync points that will need dealt with ( Resource being a key place, for example ) but there aren&#8217;t too many at the moment.  
That and I don&#8217;t particularly need that for Quirks so, that can be ignored for now.. what I DO need for Quirks is the Renderer fixed up &#8211; at the very least the Fixed Function pipeline &#8211; so I can get stuff drawing again. I then need to add Sound ( which should&#8217;ve been done last month&#8230; ) and support for more platforms than just Linux and Pandora &#8211; specifically Android, iOS and Win32 with the possibility of OS X. I do require a bit more than that, but that&#8217;ll at least let me start the game logic which I&#8217;m hoping to have the majority of done for next weekend. Hah.

Yes.. next weekend.. that&#8217;s going to be fun. That&#8217;s a major point of stress just now, and I can only hope it goes well else things are going to be up a certain creek without a paddle. That said, if it goes well, then effectively all that stress effectively disappears! Well, for a couple months at least&#8230; as then I move.

Anyway, off to work!