---
title: "Little Quirks - End of Week 1"
author: stuckie
layout: post
categories:
  - GLESGAE
  - Ludum Dare
  - October Challenge 2011
  - Random Gibberings
---
Well, it's Friday, so what have I managed to get done this week?

Sadly, not much - I still haven't started on the actual game logic, nor have I even finished the Renderer changes.
It's not that the Renderer changes have been difficult - all the rendering logic was there, it just needed moved about a bit, it's that things have just been too stressful to concentrate much.
The plus side is I should have the Renderer fixed up and running again "soon" - and I've also done some fiddlings to Resource so it can act as a shared_ptr in it's own right, as well as allow it to recast itself into other types where necessary ( for example, passing a RenderWindow into the X11 Event System and recasting it to a X11RenderWindow while keeping it within a Resource object so it dies properly when there are no more references to it. )

None of the engine is thread-safe in the slightest at the moment, though I'm not too bothered about that for now.. there are a few sync points that will need dealt with ( Resource being a key place, for example ) but there aren't too many at the moment.
That and I don't particularly need that for Quirks so, that can be ignored for now.. what I DO need for Quirks is the Renderer fixed up - at the very least the Fixed Function pipeline - so I can get stuff drawing again. I then need to add Sound ( which should've been done last month! ) and support for more platforms than just Linux and Pandora - specifically Android, iOS and Win32 with the possibility of OS X. I do require a bit more than that, but that'll at least let me start the game logic which I'm hoping to have the majority of done for next weekend. Hah.

Yes.. next weekend.. that's going to be fun. That's a major point of stress just now, and I can only hope it goes well else things are going to be up a certain creek without a paddle. That said, if it goes well, then effectively all that stress effectively disappears! Well, for a couple months at least; as then I move.

Anyway, off to work!