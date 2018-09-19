---
title: JESSIE
author: stuckie
layout: page
category: Engine
date: 2012-04-01
---

JESSIE was to be the JavaScript engine of GLESGAE.

The idea was when the Badgers was founded to do a few HTML5 games, then write a wrapper to launch them "natively" on the various platforms.
This was something already done at the time with things like appMobi, Ejecta, and Cordova, but it was closer to Ejecta in that it was taking the Canvas calls and throwing them to OpenGL.
Ejecta was however, iOS only, and I needed something a bit more cross platform. I had already started looking into this on the Pandora previously, binding to SDL instead, so knew what was involved.

JESSIE was built on SpiderMonkey ( the Firefox JavaScript engine at the time ) and I had made good progress with getting basic things to run.
However, it got shelved when I started at YoYo and I haven't looked at it since.
There's almost no point in resurrecting it as most browsers - mobile included - are pretty decent these days and even support WebGL.

But adding a layer to GLESGAE to run it through Emscripten to get it out into JavaScript.. that'd be interesting...
