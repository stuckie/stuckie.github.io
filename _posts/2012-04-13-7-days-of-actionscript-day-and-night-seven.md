---
title: '7 Days of ActionScript - Day (and Night) Seven'
author: stuckie
layout: post
categories:
  - 7 Days of ActionScript
  - Code
  - The Quest
---
I finished my little Sudoku thing the other day.

Day Seven was very productive, though due to starting late, it did drift into late night/early morning! <br />
Although I didn't get sound done ( or bitmap loading, either.. it was all drawn shapes, ) I did get a lot done, and my little Sudoku game actually worked out fairly well considering I did a crash course in ActionScript within a week.

I'll put it up soon for a giggle.

One thing that tripped me up a huge amount was variable scoping. <br />
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

You wouldn't have a problem, as anotherBool loses scope in each block.

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

You'd get an error, as anotherBool was declared in the first block. <br />
ActionScript's variables are scoped to the function. <br />
Which is really flippin' annoying when you come from a background of coding the first way!

But yes, I'm proud of my little Sudoku game, done in 7 days, in ActionScript, on Linux. <br />
It's not very fancy or pretty, but it does the job. ActionScript has a rather large amount of support code that I didn't get anywhere near ( like for Images, the preloader stuff, Audio, etc... ) so maybe I'll have a look at them next time.

Still, it was fun :)