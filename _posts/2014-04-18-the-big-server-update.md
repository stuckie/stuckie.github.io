---
title: The Big Server Update
author: stuckie
layout: post
permalink: /the-big-server-update/
categories:
  - Random Gibberings
---
Hurrah, it&#8217;s finished!

Let&#8217;s see if I haven&#8217;t missed something in the absolute chaos that ensued.

Firstly, the server was running Ubuntu 10.04&#8230; mostly.  
Due to using Matrix Panel as a configuration tool, apache, the kernel, python and a few other things were pinned to old versions.  
This had the added fun of being pretty vulnerable to DDoSing, which the server was getting hit with fairly regularly.

Obviously, not the best of things to have happen&#8230; so, the decision was made to upgrade to Debian.  
And then the fun began&#8230;

After spending about a day backing everything up, I grabbed a Debian iso and spent another day wrestling with the remote KVM implementation to try get it mounted on the server.  
No such luck.  
Thankfully, Linux can do all manner of naughty things&#8230;  
Ubuntu is also a derivative of Debian, so a quick grab of debootstrap, and a Debian bootstrap was downloaded and ready.  
Except it wasn&#8217;t quite that simple&#8230;  
As the server had been in use for a while, the partitions had all gotten used, so I couldn&#8217;t easily repartition the drive &#8211; especially as it was running, and especially since I couldn&#8217;t mount an iso to boot from.  
So I pointed grub at the bootstrap as if it was a new install, got it setup as readonly to try and use it in rescue mode to juggle the partitions about a bit, and hit the reboot button.

And it went bang.

Something had gone wrong with Grub, and as I couldn&#8217;t boot any sort of recovery disc, I was a tad stuck.  
So, I put in a rebuild request.  
Except.. they&#8217;d knocked Ubuntu off the list of things I could rebuild to.. so was stuck with CentOS 5.0 ( which was duly updated to 5.10 )

So with the server now running CentOS, and a bunch of backups that were probably a tad useless now, I was in a small pickle.  
On the plus side is that being just brought up again, I was able to repartition without any fear of killing something, even on a  running system.  
Also, VirtualBox is a godsend for fiddling about with stuff, so I setup a 64bit Debian 7 install, wedged the backup bits and pieces in and had it ticking over nicely.  
I then brought that over to the server, bit by bit, and finalized the last of it tonight.

Not that that stopped swines from attempting to DDoS the server again.. but it didn&#8217;t work, as it&#8217;ll now sort itself out and keep running, rather than bringing the whole server down.  
So, it&#8217;s taken about a week, but I&#8217;m happy with it.. it&#8217;s running much faster and more stable than it ever has.

Now to get back to Badger work.