---
layout: post
title: "Windows 10 (Nightmare Edition)"
date: 2015-09-08 00:00:00 -0000
comments: true
---

Perhaps installing Windows 10 while being ill was not the best plan...
Not only that, but on a machine which Windows 8 didn't like to install on ( the tech previews installed happily, but the final retail did not, curiously )
However, sometimes a distraction can prove welcome, and Windows 7 was getting rather slow and clogged, so a reinstall seemed a good idea.

I'd already upgraded a couple of machines to Windows 10 without issue, and they did run faster... so thought that maybe this time, it'd be plain sailing.
Nope. Straight after first reboot, it complained that something bad had happened, and to insert the install media and try again.

Great.

Ok.. so installing from scratch may not work, but I can upgrade from a Windows 7 install... so I reinstalled 7, and tried that way.
This time, it didn't even tell me it had failed with a nice error box, it just decided "nope, failed, so let's revert back to 7, whether you want to or not"
So that's a bust.

After having a quick look about, it seems there could be a few issues...
1) Drive formatted as MBR instead of GPT - so I fixed that, reinstalled, and nope...
2) USB devices acting funny - so I unplugged them all, reinstalled, and still nope...

But, I did come across an article that if there's a hardware incompatibility - due to missing drivers on the disc - it can do what I'm seeing.
My machine is rather old.. it's an Asus M2N-E SLI motherboard, 8gig ram, GeForce 550 Ti GTX ( or somewhere there abouts) and an AMD 9850 X4 Phenom Black Edition processor.
It's had all manner of Linux installed on it.. it's even had Mac OS X on it for a giggle while fiddling about.. and has been happily running Windows through XP, Vista and 7.
Surely a hardware conflict would've raised it's head by now?
Either way, I followed the instructions, which consisted of bringing up the Command Prompt (Shift + F10) when the "something bad" message appears.
Calling up regedit, then finding HKLocal machine/SYSTEM/SETUP/STATUS/ChildCompletion and setting setup.exe from 1 to 3.
This worked, and install continued happily... until the next issue...

Almost constant rebooting for apparently no reason once I got to the desktop.

One of the issues that could've been halting install was USB wifi, so I removed that and it seemed a bit more stable.. so off I went to get the driver on another machine, onto a usb stick, and install that way.
I did the same with the nVidia graphics drivers too, as that was another hiccup I had seen regularly - borked graphics drivers.
And it did seem slightly more stable.
Until it started installing updates... and the reboot-loop began again.
This seemed to be caused by a somewhat wonky update, so I removed the USB wifi again, and poked in the registry, finding HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList and deleting any with a ProfileImagePath.
And that seemed to behave itself again.. so I stupidly turned the machine off for the night after a day of wrestling with it.

That was a fun mistake.

On booting in the morning, it crashed while logging in and rebooted.
Only now, it's pretty adament I have the wrong password - even after changing it online.
So.. back to the recovery command prompt.
A run of chkdsk D: /F /R/ X ( to make sure it tried something ) took a few hours and ... nothing.
Attempted to jump to the last restore point before the update and... computer says no.
So.. it's stable at least, but I can't login and use it.
I can't boot to the recovery console on the install itself, as it wants me to login... so I can't add a new user, or activate the Admin user.
I can't use the recovery shell from the install disc to add a new user, as the net service talks to the recovery environment and not the actual install on disk.

I have been fiddling with computers from a young age - which I blame my parents on for encouraging me.
I've installed Slackware 8.1 from floppies onto a 486.
I've installed Mandrake and SuSE when nVidia just started pushing out binary drivers, and the madness that caused in system stability trying to use them.
I even got my printer and scanner working under Mandriva!
I've compiled Gentoo on an AMD Duron 1200 with a gig of ram just to see how it all worked.
I've built embedded Linux systems with Debian and LFS.
I've created cross-compiling toolchains between ARM, MIPS, x86, and x64.
I've even built runnable Windows software under Linux via WINEGCC.

All of these have been fun projects as I wanted to fiddle with them.
Never have I come up against a piece of commercial software - especially such a vital part of a computer's software infrastructure - that I've had to do such ridiculous hoop jumping just to get the bloody thing to work!
And it still doesn't!

It runs fine on the laptop I recently upgraded from 8->8.1->10.
It runs very well on the media centre I upgraded from 7->10.
It'll likely run fine on the two netbooks I have, and another one of the laptops ( if I can get it's graphics chipset fixed, anyway )
But my main desktop? Nope. Not having that.
Which makes me somewhat wary of letting it go near the Badgers work laptop as I can't really have that explode on me the way my desktop has.. it needs to stay running for those precious few minutes I can find to work on things.
As life is.. well.. life.. it gets in the way of everything...
For instance, this site is waay behind schedule of being sorted out..
The Badgers site at least runs, but I've not been able to do anything Badger related for about a year now... short of some patch work, and filing paperwork for the accountant to play with.
I can't afford time to muck about with OS installs that go haywire anymore.. I need something that works, and funnily enough Windows just doesn't make sense anymore; Linux does.

I'll have another fiddle tonight with Windows 10, to see if I can get it to stick.
But odds aren't looking good for it, and I might be back to fully Linux.

Good thing Debian 8.2 just got released, then!
