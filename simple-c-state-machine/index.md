---
title: Simple C State Machine
author: stuckie
layout: page
categories: ['Programming', 'Guide']
---
While cleaning up some of my hard drives, I found this random little snippet that I wrote as an example for someone on IRC a few months ago.

As it&#8217;s a nice clean bit of code, and rather useful, I thought I&#8217;d stick it up here so I don&#8217;t lose it!  
I therefore present to you, a very simple little State Machine, written in C, that can be expanded and uses for whatever you wish.

The following code is a working example, so just copy/paste it into a .c file, and run your compiler over it.

<pre>/* 
	Stuckie's Silly Little State Example .. let's call it SLate for a giggle.
	Coded in C for the hell of it, and it's more interesting than in C++ which gives us the use of Classes and virtual functions.
*/

#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;

/* Some globals for this little example. */
int gLoopCounter = 0;
int gUpdateState = 1;

/* 
	All important typedef for our state function. 
	We'll return an int ( negative numbers designate error values as standard C practise ) and expect a float ( deltaTime. )
	You could state this as a generic function pointer as explained here: http://www.safercode.com/blog/2008/11/25/generic-function-pointers-in-c-and-void.html
	However, you'll have lost a lot of the "WTF IS GOING ON!?"-ness of the system, therefore we're going for the good 'ol strict typedef function pointer style.
*/
typedef int(*StateFunction)(float);

/* State itself is quite simple, and mimics what you'd essentially do in C++... */
typedef struct State
{
	char* name; /* every state gets a unique name to identify it. Could choose an int or something else instead if wanted. */

	/* Technically you could have as many, or as few, state phases as you want. We'll have onEnter, update and onExit as defaults. */
	StateFunction onEnter;
	StateFunction onUpdate;
	StateFunction onExit;
} State;

/* We want to effectively only have one state active at any one point, so lets have a global here. */
State* gCurrentState;

/* May be daft to have a "createState" function when really you just need to do it yourself and plunk a few variables in, but it keeps things neat and tidy! */
State* CreateState(char* name, StateFunction onEnter, StateFunction onUpdate, StateFunction onExit)
{
	State* newState = malloc(sizeof(State));
	newState-&gt;name = name; /* obviously you want to behave yourself and do some checking here. */
	newState-&gt;onEnter = onEnter;
	newState-&gt;onUpdate = onUpdate;
	newState-&gt;onExit = onExit;

	/* 
		You may want to do something else here.. 
		I suggest storing all these states in an array or something - hence the name id - so you can pull them back out and switch between them at will.
		Whatever you do, this is where you'd do it.
	*/
	return newState;
}

/* Again, you could just modify and call stuff directly, but we want to keep some sort of sanity in the system to figure out what's going on! */
void ChangeState(State* state)
{
	int error = 0; /* Obviously, you'll want to be checking this... */

	if (gCurrentState == state) /* do nothing if we're trying to set the same state again. */
		return;

	if (gCurrentState) {
		error = gCurrentState-&gt;onExit(0.0F); /* You don't generally give a hoot about deltaTime when exiting a state, same with entering. */
		printf("Killing Old State: %s\n", gCurrentState-&gt;name);
		free(gCurrentState); /* be good and clean up after yourself! */
		gCurrentState = 0;
	}

	if (state) {
		gCurrentState = state;
		error = gCurrentState-&gt;onEnter(0.0F);
	}
}

/* With our "State System" out the way - apart from updating, but we'll get to that - we'll define some dummy functions to call. */
int outroOnEnter(float deltaTime)
{
	printf("Outro onEnter\n");

	return 0;
}

int outroOnUpdate(float deltaTime)
{
	printf("We should've effectively cleaned up now and ready to quit, so let's set the global update state to something to force a quit\n");
	gUpdateState = 0;

	return 0;
}

int outroOnExit(float deltaTime)
{
	printf("Outro onExit\n");

	return 0;
}

int gameOnEnter(float deltaTime)
{
	printf("Game OnEnter\n");

	return 0;
}

int gameOnUpdate(float deltaTime)
{
	printf("I'S DANCIN!!!\n");
	++gLoopCounter;

	return 0;
}

int gameOnExit(float deltaTime)
{
	printf("Game onExit\n");

	return 0;
}

int introOnEnter(float deltaTime)
{
	printf("Intro OnEnter\n");

	return 0;
}

int introOnUpdate(float deltaTime)
{
	printf("Intro Updating Just Once\n");
	ChangeState(CreateState("Game", gameOnEnter, gameOnUpdate, gameOnExit));

	return 0;
}

int introOnExit(float deltaTime)
{
	printf("Intro onExit\n");

	return 0;
}

int main(void)
{
	State* introState = CreateState("Intro", introOnEnter, introOnUpdate, introOnExit);
	State* outroState = CreateState("Outro", outroOnEnter, outroOnUpdate, outroOnExit);

	ChangeState(introState);
	while (gUpdateState &gt; 0) {
		float deltaTime = 0.1333F; /* Calculate this properly! */

		gCurrentState-&gt;onUpdate(deltaTime);

		if (gLoopCounter == 10) /* We've finished our game loop and signified to ourselves to quit */
			ChangeState(outroState);

	}

	if (gCurrentState) {
		gCurrentState-&gt;onExit(0.0F);
		free(gCurrentState);
		gCurrentState = 0;
	}

	return 0;
}</pre>

It&#8217;s relatively well commented as to what&#8217;s going on, so I&#8217;ll just highlight a quick little gotcha in that when the state is changed, the old state is free&#8217;d automatically. However, you could remove that and store them in an array or something so that you can access them again later and switch between them. There&#8217;s also nothing stopping you from extending it to a stack and push and pop them &#8211; running just the top state.

Either way, I thought it was a neat little bit of code to keep around anyway.