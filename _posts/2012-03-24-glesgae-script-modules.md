---
title: GLESGAE Script Modules
author: stuckie
layout: post
categories:
  - Code
  - GLESGAE
  - Ludum Dare
  - Projects
---
The past couple of months, I've been fiddling with JavaScript and writing a module for it within GLESGAE.<br />
The way I'm doing this is so that the scripting modules are effectively separate libraries, so for example, there's GLESGAEJS for the JavaScript portion, and GLESGAELua for the Lua portion.<br />
Nothing in the main library will be dependent upon it, and if you want to use GLESGAEJS, you'll need to pull in GLESGAE as well.

In terms of the JavaScript bindings, I've also been providing some support for some HTML5 elements, such as Canvas and Audio. The idea being that it can be used to power web applications as a native application, creating a hybrid application that can access both JavaScript and C++, or bridge to whatever other language you feel like ( some JavaScript/Lua mash-up, perhaps? ) <br />
I've not done any WebGL support as yet, but this should be relatively trivial, and also be a very nice fit considering the engine's designed for GLES support from the outset!

I'm still planning on getting Lua support done as well. Lua's still my favourite scripting language for it's small footprint and easy extendibility, and as long as I stick to the framework I've laid out, I should be able to fiddle with other scripting languages too. 

I had been aiming to get the engine ready for the next Ludum Dare, but with various commitments this year, it looks like I'll be missing both the April and August competitions. So, hopefully by October, I'll definitely be ready to tackle something this time!

This is looking like it'll be a good year though - so here's hoping I can find more time for random projects :)