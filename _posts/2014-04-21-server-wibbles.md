---
title: Server Wibbles
author: stuckie
layout: post
permalink: /server-wibbles/
categories:
  - Arcade Badgers
  - Random Gibberings
  - stuckieGAMEZ
---
So, the server switch didn&#8217;t go smoothly as previously posted.

Actually, having ran it a few days now, I did hit some issues.  
Most of that is to do with the multi-server shenanigans of Arcade Badgers.

It&#8217;s DNS is hosted elsewhere, it&#8217;s mail somewhere else, a VPN somewhere else and now, it&#8217;s web server another different place as well.  
Most of these were consolidated on the same server.. but what with Arcade Badgers being somewhat of a priority domain, I split off emails and DNS so that if the server had a hiccup, I could still get emails.  
When I upgraded the server, I just pulled along the VPN and web server with it&#8230; but the poor little server had issues with it, as it&#8217;s DNS isn&#8217;t quite what it thought it was, so was sometimes getting confused and then pulling down the entire server in a bit of a fit.

So, the webserver is now up on Amazon&#8217;s EC2 service&#8230; and what a rather pleasant experience it was to do.  
As it&#8217;s only going to be one instance for the one thing &#8211; hosting the site data &#8211; I was able to use the micro instance which fits with the free usage tier.  
It&#8217;s Amazon Linux appears to be a RedHat derivative what with the use of the Yum package manager, so is easy enough to deal with as the server has CentOS on it as well as a backup; another RedHat variant.

In my usual manner, I still stuffed up a couple of things on the first attempt.  
I managed to cock up the security groups and blocked access to the server from pretty much anywhere. That was silly. Thankfully you can reassign and fiddle with security groups as you see fit.  
Then it was configuring the Elastic IP thing for plugging into the DNS server and wiring up the domain properly.  
What I didn&#8217;t expect was this sortof knocked out the address I had been using to access the server, so was somewhat confused when I couldn&#8217;t get back in!

However, it&#8217;s up and running now, and hopefully will sit quite happy in the free tier for a while

That also brings us to the end of the server madness.

Till something else breaks anyway!