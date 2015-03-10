---
title: GLESGAE and YoYo
author: stuckie
layout: post
permalink: /glesgae-and-yoyo/
categories:
  - Arcade Badgers
  - GLESGAE
  - Random Gibberings
---
So, I had an interview with YoYo on Friday.  
It was interesting, being the first interview I&#8217;ve been to in a number of years, and with the added bonus of anxiety&#8230; probably came across as a gibbering monkey! And a couple of questions put me on the spot and I froze &#8211; even though they were really rather easy. Oh well, they certainly made me feel welcome enough, and I&#8217;ll find out in a few weeks if I&#8217;ve managed to get away with my cheekiness of pointing out GM:Studio doesn&#8217;t run on Linux <img src="http://stuckiegamez.co.uk/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" />

Not being one to take nothing away from any interview, it made me rethink a bit on what I&#8217;m doing with GLESGAE.  
I&#8217;m being rather lazy and relying a fair amount on STL.

Now, STL is nice and all, but it&#8217;s a specification that each compiler has to implement&#8230; and not all compilers are created equal. Earlier versions of certain compilers had rather spotty support for some STL standards, and being aware that just a simple call like *std::string myString; *can allocate more than you think!  
Actually, std::string is a funny one if you&#8217;re not sure what it&#8217;s up to&#8230;.  
It does contain a bog-standard char\* buffer for quickness. But, it&#8217;s rather small, and if your string is bigger than it&#8217;s buffer, it&#8217;ll allocate a new pointer \***somewhere else*** instead. Where that is, is anyone&#8217;s guess but the programmer shouldn&#8217;t really care&#8230; right? Of course, not all implementations will do this optimization, you may be unlucky and have it new some memory wherever it feels like anyway.  
Dealing with consoles, you have a very tight amount of memory, and you need to know exactly what is allocating where and how much it is. It&#8217;s fairly common sense to keep track of your allocations anyway, but on memory constrained devices it&#8217;s paramount &#8211; especially when the bug bear of fragmentation rears it&#8217;s ugly head; not knowing what&#8217;s where and can be safely moved around is a nightmare waiting to happen.

Therefore, to prevent such nightmare scenarios, GLESGAE is being rewritten. Again. In straight C and providing my own containers for things.  
Why?  
Because.  
Or more eloquently; there&#8217;s some nasty template hacking going on in JESSIE due to binding things with SpiderMonkey.. and it&#8217;s not nice. The only reason is for type safety, and while type safety is nice and all, having to perform odd looking things to make it work isn&#8217;t really worth it. It makes the code nasty to read, and a right bugger to maintain. GLESGAE has a few of these mad template things as well &#8211; and this is also what made the Resource System such an arse to deal with. So let&#8217;s just ignore all that and stick with C!

Also, I&#8217;m wondering about Emscripten again&#8230; do I just leave JESSIE and focus on GLESGAE and have Emscripten compile to JavaScript for browser platforms, and push directly to native platforms from GLESGAE? It&#8217;s an interesting one.. of course, I&#8217;m more interested in compiling out to JS by Emscripten, then pulling it back in through JESSIE. But I&#8217;m a lunatic.

Of course, I still have other things to do in the mean time.  
August didn&#8217;t go hugely well for the Badgers&#8230; we got our funding in, but due to schools just starting up and illnesses in the family, it&#8217;s been hard to get any work done. The Germies patch is a bit behind schedule, for instance.  
It also means there isn&#8217;t anything coming in at the moment.. so to remedy that, September is going to be an interesting month for the Badgers. We&#8217;ll be working on three games &#8211; Germies, and two others &#8211; to try get something coming in.  
We missed Ludum Dare, sadly.. which is a shame as we had an awesome idea for it, but hopefully we&#8217;ll get to the October Challenge instead and get something released then. And then by November, it&#8217;s back on to engine work in a mad push for a Christmas project.