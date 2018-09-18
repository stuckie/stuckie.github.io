---
title: 'A New Project...'
author: stuckie
layout: post
categories:
  - GLESGAE
  - Project One
  - Projects
  - Random Gibberings
---
I've had a license for Impact for a while now ( see <http://www.impactjs.com> for what this is - essentially a rather nice HTML5 engine, ) and I've even fiddled with binding enough JavaScript and HTML5 niceties to C++ in order to gain access to more exotic hardware, which may not have a capable web browser. This code has been fed back into my GLESGAE engine if you're interested in it, but it's stalled for now while I decide just what to do with GLESGAE...

GLESGAE started out as an educational tool for myself, to enable me to fiddle with render pipelines and shaders, without breaking anything at work. It then started to grow, as things often do, as a bigger engine framework thing. Then I started wedging in JavaScript, and binding up bits of Canvas and HTML5 features - and this is when I hit a nice brick wall. GLESGAE is meant primarily for GLES rendering - the OpenGL version primarily available on mobile hardware. However, ES 1 and ES 2 are far apart from one another in terms of functionality and API. <br />
One of Canvas' neat tricks is off-screen rendering. This can be implemented as a simple Render to Texture on ES2, but it's a fair bit more annoying on ES1, as there's ES1 and ES1.1 as well as Lite versions... so I ran into the wall of what to support, looked into pBuffers for a while, and then got distracted with work for a while.

Going back into that isn't what I really want to do at the moment so, in true homebrew hacker fashion, let's start another project!

Actually, two projects.. but the second one isn't going to start until the first one is complete.

Project One - as it shall henceforth be referenced as until I come up with a name - is going to be written using Impact, and be an HTML5 game. <br />
Project Two is a re-imagining of my work on GLESGAE while binding JavaScript and HTML5 Canvas, and shall not be further discussed until Project One is complete - and I shall stab myself in the hands should I attempt to start Project Two before Project One is finished. <br />
So, what is Project One? <br />
I'm not entirely sure to be honest! <br />
I have a few ideas - taking one of my LudumDare projects and redoing it in Impact. The likely subjects would be Little Quirks or Moons of Subterrane which both have a fair amount of work done on them already. There's also Tiny Critters - but if I don't do that justice, I may have questions to answer from my fiancé, so let's leave that alone for now till I have more time! <br />
There's also raiding the archives for something - which can bring out T.I.T.A.N, and Wobots. <br />
Finally, there's starting something brand spanky new.. and there's a few designs sitting about that haven't been talked about, one of which is likeliest for being Project One.

So, gibberings aside, I'm going to start a devblog of sorts for Project One, and give myself a somewhat loose deadline of - end of the month - to get it done in.

Plenty of time!

\*cough\*