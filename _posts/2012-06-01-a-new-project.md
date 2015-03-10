---
title: 'A New Project&#8230;'
author: stuckie
layout: post
permalink: /a-new-project/
categories:
  - GLESGAE
  - Project One
  - Projects
  - Random Gibberings
---
I&#8217;ve had a license for Impact for a while now ( see <http://www.impactjs.com> for what this is &#8211; essentially a rather nice HTML5 engine, ) and I&#8217;ve even fiddled with binding enough JavaScript and HTML5 niceties to C++ in order to gain access to more exotic hardware, which may not have a capable web browser. This code has been fed back into my GLESGAE engine if you&#8217;re interested in it, but it&#8217;s stalled for now while I decide just what to do with GLESGAE&#8230;

GLESGAE started out as an educational tool for myself, to enable me to fiddle with render pipelines and shaders, without breaking anything at work. It then started to grow, as things often do, as a bigger engine framework thing. Then I started wedging in JavaScript, and binding up bits of Canvas and HTML5 features &#8211; and this is when I hit a nice brick wall. GLESGAE is meant primarily for GLES rendering &#8211; the OpenGL version primarily available on mobile hardware. However, ES 1 and ES 2 are far apart from one another in terms of functionality and API.  
One of Canvas&#8217; neat tricks is off-screen rendering. This can be implemented as a simple Render to Texture on ES2, but it&#8217;s a fair bit more annoying on ES1, as there&#8217;s ES1 and ES1.1 as well as Lite versions&#8230; so I ran into the wall of what to support, looked into pBuffers for a while, and then got distracted with work for a while.

Going back into that isn&#8217;t what I really want to do at the moment so, in true homebrew hacker fashion, let&#8217;s start another project!

Actually, two projects.. but the second one isn&#8217;t going to start until the first one is complete.

Project One &#8211; as it shall henceforth be referenced as until I come up with a name &#8211; is going to be written using Impact, and be an HTML5 game.  
Project Two is a re-imagining of my work on GLESGAE while binding JavaScript and HTML5 Canvas, and shall not be further discussed until Project One is complete&#8230; and I shall stab myself in the hands should I attempt to start Project Two before Project One is finished.  
So, what is Project One?  
I&#8217;m not entirely sure to be honest!  
I have a few ideas &#8211; taking one of my LudumDare projects and redoing it in Impact. The likely subjects would be Little Quirks or Moons of Subterrane which both have a fair amount of work done on them already. There&#8217;s also Tiny Critters&#8230; but if I don&#8217;t do that justice, I may have questions to answer from my fiancé, so let&#8217;s leave that alone for now till I have more time!  
There&#8217;s also raiding the archives for something&#8230; which can bring out T.I.T.A.N, and Wobots.  
Finally, there&#8217;s starting something brand spanky new.. and there&#8217;s a few designs sitting about that haven&#8217;t been talked about, one of which is likeliest for being Project One.

So, gibberings aside, I&#8217;m going to start a devblog of sorts for Project One, and give myself a somewhat loose deadline of &#8220;end of the month&#8221; to get it done in.

Plenty of time!

\*cough\*