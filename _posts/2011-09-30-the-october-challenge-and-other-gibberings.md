---
title: The October Challenge ( and other gibberings )
author: stuckie
layout: post
categories:
  - GLESGAE
  - Ludum Dare
  - October Challenge 2011
---
Ludum Dare's October Challenge is more or less under way now.

And in true Stuckie-style, I'm not really ready for it! I still haven't managed to commit anything of what I wanted to do with GLESGAE back into the github ( though I do have multiple bits and pieces stashed around my machines ) and haven't quite settled on a distributed VCS.. well, let's sort one of them out now!

From using both Git and Mercurial ( both at work and at home, funnily enough, ) I haven't really seen a great deal of difference between the two. Granted I'm not fully embracing what each one can actually do, but from what I can see, they both act similarly enough to me to make the choice somewhat moot.
Git does seem to be somewhat more widespread than Mercurial so I'll be going with that, I think.. however knowing how to use the both of them is going to help regardless anyway.

Back to the engine then!

As my last gibberish post detailed, I'm going to be plugging a Component System into GLESGAE, and it's a fair bit of work as it requires all sorts of fiddlings and subsystems which aren't quite there yet. However, before all that, I still have to finish off what the goal of the VCS trial was all about - splitting up the RenderContexts.

Currently, GLESGAE has a handful of RenderContexts - GLES1, GLES2 and GLX - which all derive from a base RenderContext class. There's also FixedFunctionContext and ShaderBasedContext which perform the actual rendering themselves and get automatically pulled in with the other ones should they support them. This is silly, as there's an obvious divide here - PlatformContexts and RenderContexts themselves.
I have in fact split this up on my desktop machine in this very fashion already.. it just needs some more testing and tweaking, and it allows me to define at compile time for specific platforms just how I want things to be rendered.

For example:<br />
I could create a GLES1RenderPlatform, and bind a FixedFunctionVBORenderContext to it. It does what it says on the tin - renders via VBOs. However, as you may be aware, GLES 1.0 doesn't support VBOs, so for the cases where I can detect that, I replace the RenderContext with FixedFunctionVARenderContext to render through good 'ol Vertex Arrays instead. Additionally, just to add extra fun, Apple platforms support VAOs - Vertex Array Objects - which effectively save the state of the Vertex configuration into objects to be reused quicker, rather than doing all the manual enabling and disabling of Vertex Attributes - so those cases I'd have FixedFunctionVAORenderContext - and I'm guaranteed to have VBOs on there too.<br />
As you can see, it becomes rather flexible, as each RenderContext only really needs to override the drawMesh function, and perhaps some extra processing to manage VBOs and VAOs where necessary. The ShaderBased Contexts effectively work the same, and can additionally be extended to support later Desktop versions of GL with fun Geometry Shaders and so on. 
Additionally, I shall also be creating RenderTargets - which can be either the Screen itself, or an off-screen Buffer - configurable to have your choice of Colour, Depth and Stencil attachment(s)

So, with the October Challenge under way ( and a ton of work to be getting on with, ) here's my quick and rough schedule for the month.

Week One: System Stuff

  1. Finish off Render Context fiddling.
  2. Increase Platform Support to include Windows, Android and iOS.
  3. Audio.

Week Two: Make The Game!

  1. Get something rendering, moving about, and controllable on all supportable platforms.
  2. Test as many gameplay ideas as I can possibly get away with! ( I currently have three very different game ideas to attempt this month, so I shall be using Week Two to settle on one of them. )

Week Three: Finish The Game!

  1. Finalize as much of the game as I can. Obviously this'll be a bit more defined during week two.
  2. Effectively have the core game as bug-less as possible.. before going on to implement the potentially vicious parts&#8230;

Week Four: Money Makin' Integration

  1. Integrate any store-based stuff. It is the October Challenge to make $1 (yay, 69p!) after all.
  2. Of course, if doing anything like In-App Purchasing, I'll have needed to have designed for this in Week Two ;)
  3. This'll also be the week of submitting it to the various stores and setting everything up in the hope of making that fabled $1!

And on top of this, I shall be doing work related stuff as normal, so this'll be done mostly at weekends and evenings&#8230; even then, two weekends are taken up with other important things&#8230; just like a normal Ludum Dare then! Just lasts a bit longer ;)
So, hopefully I shall be posting a bit more over the following month with what I'm up to and so on with the October Challenge&#8230; and good luck to everyone else that's taking part!