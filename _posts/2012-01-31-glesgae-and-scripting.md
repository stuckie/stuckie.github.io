---
title: GLESGAE and Scripting
author: stuckie
layout: post
categories:
  - Code
  - GLESGAE
---
It's been a while since I had time to look at GLESGAE, but I had some time last night to do so.

I'm surprised that it's still relatively clean, and in a working state! But I did seem to split it and spew it across all manner of source control systems - two public SVNs, a public git, a private SVN and a private git - so finding the current version was fun.
Though from what I was up to last time with the rewriting of the graphics system, it looks like I broke shader support - but then for what I'm about to do, I'm not going to be needing that for a while yet anyway, so that can be fixed in due course.

One of the things I'm particularly partial to is that of offloading as much as I can get away with to a scripting language. This generally allows quicker iteration of ideas, and anything that slows down can (generally) be easily translated to a native function if need be - you'd just need to overload the function call!

For the most part, my language of choice has been [Lua][1].<br />
It's fast, it's small, it's very easy to embed and extend, and I've been fiddling with it for years now.<br />
I do like me a bit of Lua.<br />
Lua was going to be my first choice of implementing a scripting language into GLESGAE... however, with the rise of HTML5 and JavaScript, I'm having a slight change of heart.

The past few months, I've been looking over HTML5 and JavaScript. Having quick fiddles here and there, and playing with things like Impact, WebGL and Canvas directly. While it's been relatively painless on my development environment of choice - Linux and Chromium - it's not quite been as easy to get things running on other browsers without oddness, and especially on mobiles as generally they lag well behind their desktop counterparts, and are a much more constrained platform to work with.  
Luckily, there are several projects providing technology to help bridge this gap - such as [Appcelerator][2], and [AppMobi's various projects][3], to name a few. These work by binding JavaScript to their engine-like system, and parsing it directly without the overhead of a full browser, as well as providing a bunch of extra overloads and libraries for various things to make your web app feel and act like a native app.<br />
This is nice and all, but they also throw in everything and the kitchen sink ( the test apps for both companies are actually labelled as such too! ) whereas for doing something like games, you don't generally need as much, or would at least like to get rid of as much cruft that's not being used as you possibly can.

So, I've been thinking that the first scripting language that GLESGAE will be supporting is JavaScript.<br />
However, this brings about it's own dilemmas... supporting JavaScript isn't exactly an easy endeavour as it's more of a specification of [ECMAScript][4] than of a nice compact module or library you can just throw into your code, like Lua. As such, I've been looking at [JavaScriptCore][5] ( and the entirety of WebKit in general ) and [Google's V8][6] to use in such a manner.

V8 looks really nice and clean, and provides a C++ API - which as I'm using C++ in GLESGAE anyway, is a nice little boost.. though wrapping around C isn't exactly problematic anyway. I had examples compiling and running in a little under an hour, and felt experienced enough to take on the task of adapting a system-like interface for easily extending classes, managing contexts, etc...<br />
There is a slight hiccup though.. I haven't really found much of a way of getting it running on iOS nicely, and while GLESGAE doesn't actually support iOS at all just now, it will do in the near future.

JavaScriptCore, on the other hand, does run on iOS...; it's also already embedded in the OS to begin with as it's part of WebKit - which powers Safari. It exposes a C API to deal with binding, and while there's certainly more tutorials and examples on using it, it just doesn't feel as *clean* as V8 does. That said, it's still straight-forward enough to use.

While I really do like V8, and would much prefer to use that.. it seems that without it supporting iOS at the moment, my hands are a bit tied ( I'd love to be pointed to some help on actually getting it compiling and working on iOS without resorting to jailbreaking the device! ) So it's JavaScriptCore for me.

This will all be added to what is now going to be the main and only supported repository of GLESGAE; [The github project][7]. I may still maintain a personal one for random fiddlings, but the public engine itself shall be opensource under the LGPL v2.1 with the terms effectively summarised as:

  * You can either link via a shared object ( e.g. GLESGAE.dll ) or you can statically link.
  * If you statically link, you must either provide the object or source code to your application along with any libraries and custom tools not available with a standard platform development kit that use this code, or simply provide a written offer, valid for three years, to provide these materials upon request to anyone with a legal copy of your application.
  * If you link via shared object, just note which version (GIT Revision/Tag or Binary Release Version) you have used.
The offer of a *private* license is still open as well, should the LGPL not be to your liking.

Anyway, with that out of the way, and now knowing what I'm up to again, expect JavaScriptCore bindings in GLESGAE at some point!<br />
What? where you expecting an actual date for me to miss? :)

 [1]: http://www.lua.org
 [2]: http://www.appcelerator.com/
 [3]: http://www.appmobi.com
 [4]: http://www.ecmascript.org/
 [5]: http://www.webkit.org/projects/javascript/
 [6]: http://code.google.com/p/v8/
 [7]: https://github.com/stuckie/glesgae