---
title: Components and Resources and Data, oh my!
author: stuckie
layout: post
permalink: /components-and-resources-and-data-oh-my/
categories:
  - GLESGAE
---
One of the first big tasks I got my mitts into at work was on designing and building a Component-based system with others in our project&#8217;s code team, and due to my experience with Database writing, I got given the lovely job of dealing with that end of things.

The database systems have gone through a few changes since then, from a rather query-like system that was very flexible but perhaps to the detriment of causing certain console architectures to have a hairy fit due to the internal database structures, to a more resource managery state whereby the objects the databases maintain are just groups of arrays &#8211; or a map, if you will.

Thinking about how to do the components for GLESGAE in a manner that won&#8217;t have my hands cut off for plagiarism however, I&#8217;ve come up with a slightly different approach.

As I already have a Resource system, I may as well use that. This takes care of the storage and retrieval of both components and entities ( and I can group them as I please due to the whole template nature of the Resource system. )  
This leaves the problem of communication.

There are a number of ways of dealing with communication between entities and components, and they all define how the component system behaves. You can have components which are nothing more than data stores, and the entity itself provides the interface to it&#8217;s components. This works incredibly well for fixed entity types where you know exactly what components it is going to deal with, and you still retain the component system&#8217;s code re-usability for quickly stitching new entities together.  
Another option, and the one which I will be leaning towards, is that of the component itself actually containing logic to process it&#8217;s own data, and is ticked over by it&#8217;s parent entity. This keeps code that acts on data in the same space, further increasing the &#8220;smack components together to form an entity&#8221; idea that I like so much about component systems, as you don&#8217;t need to create an entity interface to maintain it&#8217;s components.

So how would the components talk to themselves to get the information they require to update?

Again, there are a few ideas.. from the naive and hacky &#8220;just throw a pointer link in, no-one will know!&#8221; which not only can cause bad pointer voodoo, but also makes saving state of your component data far tricker than it need be, to giving each component it&#8217;s own &#8220;mailbox&#8221; for others to post messages to it &#8211; or in my case, giving each entity a mailbox to deliver messages to it&#8217;s components or discard them as it sees fit; much like the Objective C selector gubbins.

How would this work, you ask?

Well, each entity must be unique, whereas components do not necessarily have to be unique ( think of a graphics component which has the same model data.. much more memory efficient just to link that to multiple entities, than duplicate the data inside. ) Therefore, sending messages between entities makes much more sense than to the lower level components themselves. As each component will need to be registered with the entity, it&#8217;ll know what components belong to it, and can filter messages as required.

Ah, but how do we sort these messages? and what are these messages composed of?

Well, we can give each component type a unique identifier. This limits us to one type of component per entity, however, so let&#8217;s go one further and also tag each component with a unique identifier as well, for those times we may require to talk to very specific components. We also already have a message system built in GLESGAE which works well, as all our events use it. Therefore, every entity becomes an event observer and posts all it&#8217;s components&#8217; events once it&#8217;s finished ticking them over, which&#8217;ll then get fed to each entity during the next frame.  
As for what they&#8217;ll contain, they can derive from a generic template type so they all inherit common functionality, but can additionally contain whatever extra information is required. Standard POD data in other words.

Is the event system the best option for this though, as wouldn&#8217;t every entity receive every other entity&#8217;s messages too, regardless of whether they&#8217;re for them or not?

True, every entity would receive every other entity&#8217;s message with the current event system, as that&#8217;s what it&#8217;s designed for &#8211; updating everything interested in a particular event.  
This means that our entity system needs to take some logic out of both the resource manager and the event system to work the way we want it. That and the current event system works more as a callback system in that the events get sent to all observers immediately, where as we want to batch them in this case.

That&#8217;s effectively a message system.. messages can be sent as events at any time to the event system, which doles them out to the message system. This then sorts them out on an update call, and feeds the list to whatever has registered themselves with the system. While this sounds like the same functionality as what the event system already does, we want to store every message in a giant array, and give each registered observer it&#8217;s own queue. On update, we can then sort the message array and dump each message in it&#8217;s correct queue ( or discard it ) and pass the queue on. Having that extra barrier means we can do the sorting procedure on a thread out the way, and send them off when the thread finishes.

So, what are we up to now&#8230; we require a message system for inter-component and entity communication, we need entity and component manager systems that sit on top of the resource system and tame it somewhat, and we need shells for the entities and components to derive from. What else can we get away with?

Well, as we&#8217;ve decided upon components storing logic, we can really push the component/entity logic a fair bit&#8230; an entity is an array of components; a state is an array of sub states; a sub state is an array of logic processes&#8230; now there&#8217;s a fine-grained state system that can be as granular as we like.  
The entity/component paradigm actually works for a whole load of things, especially if your components can process logic as well as store data. And, if done properly, you can serialize the data better too &#8211; something which Obj-C does very well as it&#8217;s got objects that work in the same manner.

With the Components out the way, we move on to Resources and Data.

As Resource Managers are just typed arrays of raw data, we can just load up chunks of array data without much incident. Have a header that tells the name of the group and it&#8217;s size, then dump the whole lot into the resource manager. Nice and easy.  
However, pointer data causes issues&#8230; pointers obviously won&#8217;t be pointing to the same thing when they&#8217;re serialized and reloaded, so how do we handle that? You could keep pointer data from all resources you want to serialize, or you can use lookup data ( which we already have for Resources ) which you tag into your serialized data instead of the actual pointer. This does slow down loading, as you need to parse this lookup data and rewire the pointer, however it does work.  
Another option would be to look towards a meta data solution, and there&#8217;s a few opensource variants kicking around the internet these days. Meta data is very useful, and allows all manner of arcane wizardry on the data to be performed. For the moment, however, GLESGAE won&#8217;t be using it as it requires a fair amount of work to setup and implement properly.  
Either way, we need to be able to load and save data.. so we&#8217;ll require a Resource Data Manager or something.. that can take in a typed array and either fill it from a file, or dump it out to a file.

Of course, to do that we require some agnostic file read/write utilities.. and probably some debugging utilities which I still haven&#8217;t done. Still lots of things to do yet.

And that ends what is effectively how I work out what I need to do in my engine! Complete with tense changes and all sorts!  
I sit down and think &#8220;I need this&#8230; how would I implement that? What are the knock on effects? What else can I do with it? What are the supporting systems I need? Do I have them? How do I implement them?&#8221; and so on in a recursive fashion till there are no more immediate questions, and I start to write the systems themselves. Madness? Perhaps.. but it&#8217;s worked for me so far!

&nbsp;

As for the Git vs Mercurial experimentation, we&#8217;ve actually switched to Mercurial at work so I can evaluate them both for the rest of the month with Git for GLESGAE and Mercurial for work stuff. So that works out, seeing as I still haven&#8217;t done what I originally planned to do for this month, and with not much of the month left, it&#8217;s getting a bit tight. That and I&#8217;ve just added a bunch more work to myself with what the gibberish above describes!

Ah well, keeps things interesting.