---
lastmod: 2016-09-27
date: 2016-09-04
linktitle: Introduction
menu:
  main:
    parent: getting started
next: /overview/quickstart
title: Introduction
weight: 5
---

## What is 1Bitsy?

1Bitsy is an embedded hardware/software development platform. With several main goals:

1. Small size (38.1mm x 17.8mm or 1.5in x 0.7in) and low cost allowing you to embed the hardware inside your project and leaving it as part of it.
2. Great debugging tools and simple and thin programming interfaces, making it very easy to understand how it works.
3. Easy prototyping, you can cut and paste together the examples to get going very fast.
4. Lot's of tutorials, example projects and documentation, so you can choose your own path in learning embedded hardware development. (We are always looking for new examples and projects to be added to our collection. Here is how to [contribute](/community/contributing/).)

## How is 1Bitsy different?

I know you are wondering, "Why should I use 1Bitsy instead of
something else?"

There are hundreds of different development platforms out there. Every
combination of small, large, cheap, expensive with proprietary or open source
toolchains. But when when we were looking for a board that we could recommend to
explore the possibilities of the [Black Magic Probe JTAG/SWD programmer and
debugger](http://github.com/blacksphere/blackmagic) we could not find anything
that would fit the bill, and we could recommend with good conscience. So we set
out to create a hardware and software platform that will fit the following list
of requirements:

* Small
* Affordable
* Easy to start with
* Exposes the JTAG interface (and has the JTAG connector populated)
* Open Hardware
* Does not waste space and money with an integrated debugger or USB to serial
  adapter (we want to be able to reuse the programmer and debugger, and not have
  to skimp on the quality of the debugger because it has to be included on every
  development board)
* Is software agnostic (you can develop for it with command line tools or your favorite IDE)
* Has tested and maintained set of open source development tools and libraries
* Can be plugged into a breadboard for quick prototyping

This is why we created 1Bitsy. We hope you will like it as much as we do!  :)

## How is 1Bitsy simpler?

First and foremost by exposing the JTAG debugging and programming interface and
making the [Black Magic Probe](http://github.com/blacksphere/blackmagic) our
default programming and debugging tool. JTAG is a very powerful tool, together
with the [Black Magic Probe](http://github.com/blacksphere/blackmagic) it is
also very easy to use. The JTAG interface gives you unprecedented control and
insight over your firmware.

Second are tutorials, documentation and community. By guiding you and giving you
lot's of reading resources you will be able to understand how the 1Bitsy works,
and if you are really stuck you can always ask someone.

Third by exposing all aspects of the hardware and software to you and not hiding
things behind opaque interfaces we hope you will be able to grasp how everything
works. Making it's inner workings clear.

## What software does 1Bitsy support?

1Bitsy can be programmed using one of the following solutions:

* command line + gcc-arm-embedded + libopencm3 <small>(Supports JTAG debugging)</small>

We are also planning to support the following platforms:

* PlatformIO (libopencm3) <small>(Command line JTAG debugging)</small>
* ChibiOS <small>(Command line JTAG debugging)</small>
* stm32duino <small>(No JTAG debugging)</small>
* Arduino IDE <small>(No JTAG debugging)</small>
* Micropython <small>(No JTAG debugging)</small>

## Why did you design 1Bitsy?

I really like developing embedded systems. You can use all the hardware
resources, you can comprehend the whole system, and everything that is going on.
You don't have to unravel why and how the Linux, Windows, MacOS kernel is not
doing what you think it should. Instead you just set a few bits in registers and
the hardware will do exactly what you told it to do. The only person you can
blame if anything goes wrong is you and no one else. This is a very liberating
feeling, the only thing you have to question is the hardware in front of you
(that you can probe with some basic tools like multimeter, oscilloscope and
logic analyzer) and your own code.

But what happens when you are stuck and really don't know what is going on? It
depends on what hardware platform you are using. If it is an Arduino you will
start adding `print` that output what is going on. You will then spend some time
trying to understand what the program does based on the output. Generating
output can very easily alter the functionality of your system that likely relies
on strict timing. This is when you start using an LED for debugging but if you
are trying to convey more complicated information you will need to use an
oscilloscope or logic analyzer because your eyes are not fast enough to register
the LED. Thus you will advance to the even cruder solution and start blinking an
LED but if your code is running too fast you will probably have to attach an
oscilloscope or logic analyzer to see what is going on. If you are like me you
will get the feeling of trying to debug by poking a stick into a dark pit.

But what if you give up ultimate control over the hardware and turn to a board
running a full operating system like a Linux computer. If you are in trouble you
can start your program in GDB (GNU Debugger) run the program to the point where
you encounter your issue, and using breakpoints and variable prints and watches
you can inspect your program until you find out what is happening. Very easy,
but you gave up all the best parts of using an embedded system: __ultimate
control__. :)

Why can't we have both things at the same time, ultimate control and easy
debugging? Well we actually can have both. Most modern microcontrollers come
with an interface called JTAG (Joint Test Access Group) or a smaller pin count
counterpart like C-JTAG or SWD. This interface allows you to have __godlike__
control over your hardware. Thus you can really nicely program and debug the
device you are working on. The problem is that interfacing with it is usually
problematic as you either need expensive proprietary software or an Open Source
tool that is difficult to set up.

A few years ago Gareth McMullin created the [Black Magic
Probe](http://github.com/blacksphere/blackmagic). Its a hardware device that
implements all the magic of JTAG while enabling you to easily connect it to your
hardware and your computer without a lot of hassle. (I and many others really
love the device.) After using it for several years now I realized that most
people still don't know about it. I also realized that part of the problem is a
lack of good reference projects and evaluation/development boards that can
easily take advantage of the Black Magic Probes abilities.

This is why I decided to create 1Bitsy. The goal is to create example projects,
tutorials and a hardware platform that can take full advantage of JTAG and the
[Black Magic Probe](http://github.com/blacksphere/blackmagic) hardware.


&mdash; Piotr Esden-Tempski (@esden)

## Next Steps

 * [Buy 1Bitsy](http://1bitsquared.com/products/1bitsy)
 * [Buy a Black Magic Probe](http://1bitsquared.com/products/black-magic-probe)
 * [Quick start](/overview/quickstart/)
 * [Join the Mailing List](/community/discourse-forum/)
 * [Star us on GitHub](https://github.com/1bitsy)
 * [Discussion Forum](http://discuss.1bitsy.org/)
