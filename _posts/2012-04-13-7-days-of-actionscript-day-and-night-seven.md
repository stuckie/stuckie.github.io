---
title: '7 Days of ActionScript &#8211; Day (and Night) Seven'
author: stuckie
layout: post
permalink: /7-days-of-actionscript-day-and-night-seven/
categories:
  - 7 Days of ActionScript
  - Code
  - The Quest
---
I finished my little Sudoku thing the other day.

Day Seven was very productive, though due to starting late, it did drift into late night/early morning!  
Although I didn&#8217;t get sound done ( or bitmap loading, either.. it was all drawn shapes, ) I did get a lot done, and my little Sudoku game actually worked out fairly well considering I did a crash course in ActionScript within a week.

I&#8217;ll put it up soon for a giggle.

One thing that tripped me up a huge amount was variable scoping.  
Usually, variable scope is to the current code block.. so if you were to do:

<pre>void myFunction(const bool inputBool) {
    bool myBool(false);
    if (true == inputBool) {
        bool anotherBool(true);
        myBool = true;
    } else {
        bool anotherBool(false);
        myBool = false;
    }
}</pre>

You wouldn&#8217;t have a problem, as anotherBool loses scope in each block.

However, doing something like:

<pre>public function myFunction(inputBool:Boolean):void {
    var myBool:Boolean = false;
    if (true == inputBool) {
        var anotherBool:Boolean = true;
        myBool = true;
    } else {
        var anotherBool:Boolean = false;
        myBool = false;
    }
}</pre>

You&#8217;d get an error, as anotherBool was declared in the first block.  
ActionScript&#8217;s variables are scoped to the function.  
Which is really flippin&#8217; annoying when you come from a background of coding the first way!

But yes, I&#8217;m proud of my little Sudoku game, done in 7 days, in ActionScript, on Linux.  
It&#8217;s not very fancy or pretty, but it does the job. ActionScript has a rather large amount of support code that I didn&#8217;t get anywhere near ( like for Images, the preloader stuff, Audio, etc&#8230; ) so maybe I&#8217;ll have a look at them next time.

Still, it was fun <img src="http://stuckiegamez.co.uk/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />