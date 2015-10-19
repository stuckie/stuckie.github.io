---
layout: post
title: "Plight of the Weedunks"
date: 2015-10-19 21:50:00 -0000
comments: true
---

So I've just stuck up the (almost) entire source of Plight of the Weedunks to Github: [http://github.com/stuckie/plightoftheweedunks](http://github.com/stuckie/plightoftheweedunks).
It's missing the amBX code, but you don't need that anyway... and the DLLs we had for it have long since expired.

Why put it up now?

Firstly, I lost it.

I only just found it while pouring over some backup archives, pulling together lost bits of projects - of which I've started and abandoned a huge amount of.
Also, it's got some rather interesting bits and pieces in there... it binds Horde3D, ODE and Lua together.. the vast amount of gameplay logic is written in Lua, and from what I remember, we actually *tick* the engine over from Lua as well.
It also has some quite horrendous coding practices, before I settled on anything remotely readable... but shh...

Secondly, it's important.

As I said, I lost it... and that's quite a big chunk of code to lose, and especially something that maybe not culturally important, but it's certainly important in my own programming history.
It's also quite old now, and not entirely useful to a lot of people these days, so hopefully I haven't ruffled too many feathers over at Dare to be Digital as technically they likely still own the rights to it ( though I do believe our team leader was attempting to get them a while back, and the rest of us had agreed - me on provision of being able to release the code - but not sure how that went... )
Either way, the art assets are missing - I never had a copy of the source archive. The ones here are compiled and built for the game, so will be pretty difficult to use or modify for other things.

Anyway, some choice bits of the code to look at.

The Converter was modified slightly to pull in some more information that we were spitting out of Maya ( I don't have the Maya bits we wrote - that was in the Art repository, which I never grabbed... )
Most useful bit being in https://github.com/stuckie/plightoftheweedunks/blob/master/ConverterSource/Source/Collada%20Converter/converter.cpp around lines 1038 - 1351 .. where I start spitting out Lua files for lights, cameras and chunks of level code.
This helped immensely as it let our artists and level designer set where everything was in Maya, and we just picked it up on our end and started writing logic around it.
It did however have the huge caveat that if the level changed, so too did all the scripts.. and that caught us out a few times until we started chunking up the logic better.

Other fun things are that all the ODE collision information got passed out to Lua.
So when something collided, Lua was triggered to see what to do with it.
Vast majority of the time it would be nothing, but we were able to trigger sounds ( or amBX effects! ) and bounce things off one another and so on.
I'm still surprised how well it worked.
Again, all of ODE was bound out.. if you check the level loading scripts ( we'll take Toothy as an example; https://github.com/stuckie/plightoftheweedunks/blob/master/source/data/scripts/levels/toothy/physics/static/toothy.physics.static.lua ) they're all split into scripted, dynamic and static.
We then just call ODE to bind the dimensions out properly... most of which got spat out by the converter.

We also effectively bound out all of Horde3D to Lua as well, so we were able to poke at the rendering pipeline from within Lua.
For example, https://github.com/stuckie/plightoftheweedunks/blob/master/source/data/scripts/misc/engineSetup.lua actually sets up the resource paths for Horde3D, and I vaguely remember Lachlan doing some crazy shader stuff at some point through Lua as well, before we dropped the HDR pipeline completely.

It certainly has got me thinking about crazy projects to try with GameMaker...


I've been unearthing lots of old projects while digging around archives, so I'll be trying to get them up on GitHub as well.
It would be a shame to lose them entirely, as almost happened here!