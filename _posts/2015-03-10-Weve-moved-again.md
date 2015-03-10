---
layout: post
title: "We've moved again!"
date: 2015-03-10 22:15:06 -0000
comments: true
---

So, let's see if this thing works at all...

I'm getting a bit fed up with the server going down a lot recently.. which seems to be Wordpress' bulkiness just being that bit much for the (in all honesty, aging) server.
So lets start migrating away from it as best we can.

First up, bye bye Wordpress, and hello Jekyll.
Jekyll is a static site generator... feed it some stuff and it'll spit out html based on templates and things. Nifty.
I was just using Wordpress to basically log in, type some stuff, and leave it alone for a while... I stripped out Apache, stuffed in nginx, and various caching things to make it all run faster as the generation time for the pages was getting a bit much.. now, it's all static. There's no reason for it not to be static, and technically never was, so yay! Bye bye Mysql as well!
Of course, I still need to edit the posts and create new ones.. so, let's move the site over to github, and host it from there, with images elsewhere.

No, seriously.

The blog is now on Github.

Not everything has been sorted out yet, and this likely won't be live on the main domain for a bit, but those who poke about will at least see this and understand what I've done and why.

Don't get me wrong, I enjoyed using Wordpress.. but it's a bit overkill for me to type stuff now and then, and have it constantly regenerate pages for little reason. Just eating processor time for the sake of it, really.

The Badgers site will be moving to Jekyll as well, and probably the same setup, but that'll take a wee bit longer to sort out.
