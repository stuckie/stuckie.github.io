---
title: "A quick nod to the GP32"
author: stuckie
layout: post
categories: Gibberings
---
The GP32 is always going to hold a special place in my collection for being the machine that introduced me to homebrew in the first place.

I got mine just as the machine was opened up properly to be able to do it, and a flurry of devs jumped on it to produce all sorts of things. It was great as there was always something new appearing every other day, and it certainly wasnt any slouch of a machine at the time either! But it was the fact that this was an actual hand held console that you could get a compiler and SDK for, and could make your own stuff on it that attracted me to it, and got me into this whole thing to begin with. So, my beloved GP32, this is for you!

I was asked recently to help port something over to the humble GP32, and nostalgia being the rose-tinted maiden that it is, I thought "oh it'll just be a quick recompile after I dust off my toolchain again!"  This wasn't quite the case, especially as said toolchain hadn't been touched since 2004 and didn't quite work any more.<br />
So, I thought I'd go use the excellent devkitARM which supports a few of the Nintendo hand held consoles as well. However, this also hit problems as most of the libraries I could find weren't EABI version as devkitARM was, and as I didn't have a great deal of free time to go poking at it too much, I sadly had to drop it and try another route. I'll probably come back to doing it "properly" with devkitARM as I much prefer their setup, but for now, method two will do.

Method two involved building my own arm-elf tool chain, using the rather succinct instructions over on cobbleware <http://www.cobbleware.com/gp32/gp32toolchain.html> which got me up and running pretty quickly. I did substitute GCC 3.3.6 for 3.3.2, however, and had to pull down 3.4 on my Debian box in order to compile it. I did get it compiling both on my 64bit desktop, and a 32bit laptop without issue, though, so it's certainly still feasible these days to build tool chains for older platforms as needed. I did attempt to substitute higher versions of binutils, GCC and newlib, but they died during compilation and again, lack of time to do it properly meant I just wanted something that worked.
Once I had the compiler though, my problems weren't over yet.

It seems that everyone built their own tool chain setup back on the GP32 and all manner of libraries and strange things floated about. In general though, people either wrote their own low level SDK, used the excellent Mr Mirko's SDK, or the wonderful Chui's SDL port. The devkitARM tool chain comes with Mr Mirko's SDK so if I only needed that, I'd have kept with it. I needed SDL support, however! and I had two options open to me; cobbleware's version and SDL4GP32 - <http://sdl-gp32.sourceforge.net/> . As said, everyone seemed to do their own SDK setup, and both of these sets of libraries overload a bit more than they probably should. The cobbleware version overloads stdio which caused some interesting errors in stderr and stdout not really being available, and though I got these fixed and the project compiling, I couldn't get it to work no matter how much I prodded it. The SDL4GP32 version required a bit more poking, but it did manage to work, and with a few hours remembering that the GP32 uses SMC card, which has an 8.3 filename restriction, I managed to get the project up and running with minimal changes at between 20-30fps out of 60. Not bad for a few hours work, I think!

Of course, the GP32 being the old and odd beastie that it is, most games are just not written for it these days. It's not a huge fan of large textures, and passing textures back and forth across the memory bus probably isn't going to help it much so to get that framerate up further there'd probably need to be a bit more re-organisation of the sprites and assets than I was really wanting to do. Not out of laziness, but more out of not fiddling with someone else's project! I just wanted to show them how to get it up and running on the GP32 as quick as possible, and let them sort out the issues in a way that works for them.

Anyway, this means that the first part of The GP32 Quest has been done - the tool chain.
You can find a quickly written guide over on the left.

Now, if only I was brave enough to attempt a screen replacement on my little 'ol Non-Lit GP32!
