---
title: The October Challenge ( and other gibberings )
author: stuckie
layout: post
permalink: /the-october-challenge-and-other-gibberings/
categories:
  - GLESGAE
  - Ludum Dare
---
Ludum Dare&#8217;s October Challenge is more or less under way now.

And in true Stuckie-style, I&#8217;m not really ready for it! I still haven&#8217;t managed to commit anything of what I wanted to do with GLESGAE back into the github ( though I do have multiple bits and pieces stashed around my machines ) and haven&#8217;t quite settled on a distributed VCS.. well, let&#8217;s sort one of them out now!

From using both Git and Mercurial ( both at work and at home, funnily enough, ) I haven&#8217;t really seen a great deal of difference between the two. Granted I&#8217;m not fully embracing what each one can actually do, but from what I can see, they both act similarly enough to me to make the choice somewhat moot.  
Git does seem to be somewhat more widespread than Mercurial so I&#8217;ll be going with that, I think.. however knowing how to use the both of them is going to help regardless anyway.

Back to the engine then&#8230;

As my last gibberish post detailed, I&#8217;m going to be plugging a Component System into GLESGAE, and it&#8217;s a fair bit of work as it requires all sorts of fiddlings and subsystems which aren&#8217;t quite there yet. However, before all that, I still have to finish off what the goal of the VCS trial was all about &#8211; splitting up the RenderContexts.

Currently, GLESGAE has a handful of RenderContexts &#8211; GLES1, GLES2 and GLX &#8211; which all derive from a base RenderContext class. There&#8217;s also FixedFunctionContext and ShaderBasedContext which perform the actual rendering themselves and get automatically pulled in with the other ones should they support them. This is silly, as there&#8217;s an obvious divide here &#8211; PlatformContexts and RenderContexts themselves.  
I have in fact split this up on my desktop machine in this very fashion already.. it just needs some more testing and tweaking, and it allows me to define at compile time for specific platforms just how I want things to be rendered.  
For example:  
I could create a GLES1RenderPlatform, and bind a FixedFunctionVBORenderContext to it. It does what it says on the tin &#8211; renders via VBOs. However, as you may be aware, GLES 1.0 doesn&#8217;t support VBOs, so for the cases where I can detect that, I replace the RenderContext with FixedFunctionVARenderContext to render through good &#8216;ol Vertex Arrays instead. Additionally, just to add extra fun, Apple platforms support VAOs &#8211; Vertex Array Objects &#8211; which effectively save the state of the Vertex configuration into objects to be reused quicker, rather than doing all the manual enabling and disabling of Vertex Attributes &#8211; so those cases I&#8217;d have FixedFunctionVAORenderContext&#8230; and I&#8217;m guaranteed to have VBOs on there too.  
As you can see, it becomes rather flexible, as each RenderContext only really needs to override the drawMesh function, and perhaps some extra processing to manage VBOs and VAOs where necessary. The ShaderBased Contexts effectively work the same, and can additionally be extended to support later Desktop versions of GL with fun Geometry Shaders and so on.  
Additionally, I shall also be creating RenderTargets &#8211; which can be either the Screen itself, or an off-screen Buffer&#8230; configurable to have your choice of Colour, Depth and Stencil attachment(s)

So, with the October Challenge under way ( and a ton of work to be getting on with, ) here&#8217;s my quick and rough schedule for the month.

Week One: System Stuff

  1. Finish off Render Context fiddling.
  2. Increase Platform Support to include Windows, Android and iOS.
  3. Audio.

<div>
  Week Two: Make The Game!
</div>

<div>
  <ol>
    <li>
      Get something rendering, moving about, and controllable on all supportable platforms.
    </li>
    <li>
      Test as many gameplay ideas as I can possibly get away with! ( I currently have three very different game ideas to attempt this month, so I shall be using Week Two to settle on one of them. )
    </li>
  </ol>
  
  <div>
    Week Three: Finish The Game!
  </div>
  
  <div>
    <ol>
      <li>
        Finalize as much of the game as I can. Obviously this&#8217;ll be a bit more defined during week two.
      </li>
      <li>
        Effectively have the core game as bug-less as possible.. before going on to implement the potentially vicious parts&#8230;
      </li>
    </ol>
    
    <div>
      Week Four: Money Makin&#8217; Integration
    </div>
    
    <div>
      <ol>
        <li>
          Integrate any store-based stuff. It is the October Challenge to make $1 (yay, 69p!) after all.
        </li>
        <li>
          Of course, if doing anything like In-App Purchasing, I&#8217;ll have needed to have designed for this in Week Two <img src="http://stuckiegamez.co.uk/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" />
        </li>
        <li>
          This&#8217;ll also be the week of submitting it to the various stores and setting everything up in the hope of making that fabled $1!
        </li>
      </ol>
    </div>
    
    <div>
      And on top of this, I shall be doing work related stuff as normal, so this&#8217;ll be done mostly at weekends and evenings&#8230; even then, two weekends are taken up with other important things&#8230; just like a normal Ludum Dare then! Just lasts a bit longer <img src="http://stuckiegamez.co.uk/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" />
    </div>
    
    <div>
      So, hopefully I shall be posting a bit more over the following month with what I&#8217;m up to and so on with the October Challenge&#8230; and good luck to everyone else that&#8217;s taking part!
    </div>
  </div>
</div>