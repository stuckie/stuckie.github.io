---
title: GP32 Toolchain
author: stuckie
layout: page
categories: ['GP32', 'Guide']
---
Getting the GP32 Toolchain up and running was fairly straight forward, but had a few oddities and set backs.

Currently, I&#8217;m using a self-compiled toolchain created using the guide from cobbleware; which shall be repeated more or less here for safe keeping. Original content here: [http://www.cobbleware.com/gp32/gp32toolchain.html][1]  
I&#8217;m aiming to get back to using devkitARM as I much prefer their setup&#8230; just need time to figure out what went wrong.

Anyway, to get the toolchain up and running from scratch, you effectively need to build GCC, binutils and newlib.  
On newer systems, this can be easier said than done when you&#8217;re targeting older hardware with older toolchains.  
Cobbleware was targeting GCC 3.3 series, so I followed suite.  
Running Debian Squeeze 64bit on my main box, I pulled in the Lenny repos and grabbed GCC 3.4 which allowed me to compiled GCC 3.3.6 without issue, so it&#8217;s wise to acquire that through your distribution&#8217;s package system first.

So, I grabbed GCC-3.3.6, binutils 2.14, and newlib 1.11.0 from the mirror.ac.uk repository of the GNU project. Mirrors available here: [http://gcc.gnu.org/mirrors.html][2]

I extracted all of that to a temporary folder and built binutils first with the following commands:

<pre>tar -xvjf binutils-2.14.tar.bz2
cd binutils-2.14
mkdir build
cd build
export CC=gcc-3.4
../configure --prefix=/opt/toolchains/gp32 --target=arm-elf
make
su
&lt;... enter root password ...&gt;
make install
exit</pre>

You can delete binutils now at this point.

Cobbleware created a handy script to compile GCC and newlib together, which I&#8217;ve effectively recreated below, modifying the path from /usr to /opt/toolchains/gp32

<pre>#!/bin/sh

make clean

CFLAGS="-O3 -pipe" ../configure --prefix=/opt/toolchains/gp32 --target=arm-elf --enable-languages=c,c++ --with-newlib --disable-multilib --with-gnu-ld --with-gnu-as

make all \
  CFLAGS_FOR_TARGET="-DTAG_CFLAGS_FOR_TARGET -march=armv4t -marm -msoft-float -ffast-math -fshort-enums -mstructure-size-boundary=8 -mthumb-interwork -O2" \
  CXXFLAGS_FOR_TARGET="-DTAG_CXXFLAGS_FOR_TARGET -march=armv4t -marm -msoft-float -ffast-math -fshort-enums -mstructure-size-boundary=8 -mthumb-interwork -O -fno-implicit-templates" \
  LIBCFLAGS_FOR_TARGET="-DTAG_LIBCFLAGS_FOR_TARGET -march=armv4t -marm -msoft-float -ffast-math -fshort-enums -mstructure-size-boundary=8 -mthumb-interwork -O2" \
  LIBGCC2_CFLAGS="-DIN_GCC -DCROSS_COMPILE -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -isystem ./include  -Dinhibit_libc -fno-inline -DTAG_LIBGCC_FLAGS -march=armv4t -marm -msoft-float -mthumb-interwork -O2 -ffast-math -fshort-enums -mstructure-size-boundary=8"</pre>

With this saved in the same folder as the tarballs and made executable, I then compiled GCC:

<pre>tar -xvzf newlib-1.11.0.tar.gz
tar -xvjf gcc-3.3.2.tar.bz2
cd gcc-3.3.2
ln -s ../newlib-1.11.0/newlib .
mkdir build
cd build
../../bgcc
su
&lt;... enter root password ...&gt;
make install
exit</pre>

You can wipe out the temp folder now.

Now, SDL4GP32 seems to be a better set of libraries than Cobbleware&#8217;s as they don&#8217;t seem to overload bits of the core libraries, but I&#8217;m sure both of them have their place, so I just installed them both into separate folders. These went directly into /opt/toolchains/gp32 as sdl4gp32 and gp32libs. I then created a bash script to fix up the paths and exports which ran like this:

<pre>#!/bin/bash

export PATH=$PWD/bin:$PATH
export SDL4GP32=$PWD/sdl4gp32
export GP32LIBS=$PWD/gp32libs

/bin/bash</pre>

I could then modify the make files of the examples to point to the right export path and they all compiled and worked without issue.

I&#8217;ll write up another little guide on getting stuff running on the GP32 and some gotchas I found, soon.

 [1]: http://www.cobbleware.com/gp32/gp32toolchain.html "http://www.cobbleware.com/gp32/gp32toolchain.html"
 [2]: http://gcc.gnu.org/mirrors.html "http://gcc.gnu.org/mirrors.html"