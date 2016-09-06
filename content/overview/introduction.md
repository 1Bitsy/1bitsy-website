---
lastmod: 2016-09-04
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

1. Small size and low cost allowing you to embed the hardware inside your project and leaving it as part of it.
2. Great debugging tools and simple and thin programming interfaces, making it very easy to understand how it works.
3. Easy prototyping, you can cut and paste together the examples to get going very fast.
4. Lot's of tutorials, example projects and documentation, so you can choose your own path in learning embedded hardware development.

## How is 1Bitsy different?

I know what you are most curious about. "Why should I use 1Bitsy instead of
something else?"

There are hundreds if not thousands different development platforms out there.
There are cheap boards that are large, there are small boards that are
expensive, there are small and cheap and you can download software for free but
it is closed source and locks you into one specific microcontroller. There are
small, cheap, simple boards with large communities that try to be simple by
obscuring and hiding functionality. But as far as we know there is nothing out
there that fits the following categories at the same time:

* Small
* Affordable
* Easy to start with
* Exposes the JTAG interface (and has the JTAG connector populated)
* Is OpenHardware
* Does not waste space and money with an integrated debugger or USB to serial adapter
* Is software agnostic (you can develop for it with command line tools or your favorite IDE)
* Has tested and maintained set of open source development tools and libraries
* Can be plugged into a breadboard for quick prototyping

This is why we decided to create 1Bitsy and we hope you will like it as much as we do! :)

<!--Scratch:-->

<!-- Embedded hardware development platforms divide into two
categories. Hobbyist and Professional.

_Professional_ platforms are very versatile but come at a high pricetag and are
so complicated that you can write a PHD about each one of them. The evaluation
boards are very expensive and large. Making them impractical if you want to make
them part of a device you are making. The assumption is that you will end up
designing your own hardware anyways, and you work for a company that can justify
paying thousands for the tools as they are cheaper than the engineer time.

_Hobby/artist_ platforms are smaller and simpler, but usually they achieve that
by hiding most of the functionality under a thick layer of "simple APIs"
(Application Programming Interfaces). To make a prototype you can very quickly
download a sketch from a forum and make a prototype. But more often than not, as
soon as you want to make your prototype into the real thing you end up rewriting
everything in assembly, so that it fits onto your tiny 8bit microcontroller. -->

<!-- 1Bitsy will not hide anything from you to create an illusion of simplicity. We
will rather give you all the tools, documentation and tutorials so the 1Bitsy is
simple to understand. Our philosophy is that if you actually understand the
device that you are working with and have good tools to make them transparent,
embedded systems __become__ simple. There is no need to create abstraction
layers to hide anything. This is why you are using a microcontroller instead of
a computer board like the Raspberry PI in the first place. Adding layers of
unpenetrable abstraction to make things "simple" seems counter intuitive.-->

<!-- The big advantage of microcontrollers vs computer boards that run full fledged
operating systems is that you are the GOD of the hardware and you have full and
unlimited control, so hiding and "simplifying" them is a step into the wrong
direction.-->

## How is 1Bitsy simpler?

First and foremost by exposing the JTAG debugging and programming interface and
making the Black Magic Probe our default programming and debugging tool. JTAG is
a very powerful tool, together with the Black Magic Probe it is also very easy
to use. The JTAG interface gives you unprecedented control and insight over your
firmware.

Second are tutorials, documentation and community. By guiding you and giving you
lot's of reading resources you will be able to understand how the 1Bitsy works,
and if you are really stuck you can always ask someone.

Third is exposing all aspects of the hardware and software to you. By not hiding
things behind opaque interfaces we hope you will be able to grasp how everything
works. Making it's inner workings clear.

## What software does 1Bitsy support?

1Bitsy can be programmed using one of the following solutions:

* command line + gcc-arm-embedded + libopencm3 <small>(Supports JTAG debugging)</small>
* PlatformIO (libopencm3) <small>(Supports JTAG debugging)</small>

We are also planning to support the following platforms:

* ChibiOS <small>(Supports JTAG debugging)</small>
* stm32duino <small>(No JTAG debugging)</small>
* Arduino IDE <small>(No JTAG debugging)</small>
* Micropython <small>(No JTAG debugging)</small>

## Who should use 1Bitsy?

1Bitsy is for people that prefer honesty over fake simplicity.

1Bitsy is for people that want to learn and control the hardware they work with.

## Why did you design 1Bitsy?

I really like developing embedded systems. You can use all the hardware
resources, you can comprehend the whole system, and everything that is going on.
You don't have to unravel why and how the linux, windows, MacOS kernel is not
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
on strict timing. Thus you will advance to the even cruder solution and start
blinking an LED but if your code is running too fast you will probably have to
attach an oscilloscope or logic analyzer to see what is going on. If you are
like me you will get the feeling of trying to debug by poking a stick into a
dark pit.

But what if you give up ultimate control over the hardware and turn to a board
running a full operating system like a linux computer. If you are in trouble you
can start your program in GDB (GNU Debugger) run the program to the point where
you encounter your issue, and using breakpoints and variable prints and watches
you can inspect your program until you find out what is happening. Very easy,
but you gave up all the best parts of using an embedded system: __ultimate
control__. :)

Why can't we have both things at the same time, ultimate control and easy
debugging? Well we actually can have both. Most modern microcontrollers come
with an interface called JTAG (Joint Test Access Group). This interface allows
you to have __godlike__ control over your hardware. Thus you can really nicely
program and debug the device you are working on. The problem is that interfacing
with it is usually problematic as you either need expensive proprietary software
or an OpenSource tool that is difficult to set up.

A few years ago Gareth McMullin created the Black Magic Probe. Its a hardware
device that implements all the magic of JTAG (in it and you can very) while enabling you to easily
connect it to your hardware and your computer without a lot of hassle. (I and
many others really love the device.) After using it for several years now I
realized that most people still don't know about it. I also realized that part
of the problem is a lack of good reference projects and evaluation/development
boards that can easily take advantage of the Black Magic Probes abilities.

This is why I decided to create 1Bitsy. The goal is to have/create example projects,
tutorials and a hardware platform that can take full advantage of JTAG and the
Black Magic Probe hardware.

<!-- Scratch -->

<!--It is an interface that you can connect a probe to and allow your computer to
interrupt your microcontroller and take over control in a real GOD like manner.
You can do EVERYTHING!!! Change memory, access registers, inject code, set
breakpoints, watch variables and much much much more. But why don't we know
about it, you ask. That is a very good question. But I think the main reason is
that the original Arduino Uno does not have a JTAG interface. There are Atmel
AVR microcontrollers with JTAG but they are much larger and more expensive than
what the inventors of Arduino were willing to put into their boards.-->

<!--Today most ARM microcontrollers do have JTAG but the Arduino boards that have
that interface don't even have the connector populated. You can solder on your
own connector, and cobble together an FTDI based probe and figure out how to get
OpenOCD to actually work to get debugging working, or you buy a four figure
license for one of the commercial embedded development IDE. But that is making
something that should be simple overly complicated.-->

<!--But there is a solution. It is called the Black Magic Probe. It removes the
trouble of setting up OpenOCD. All you need to do is to plug it into your
Microcontroller's JTAG connector on one end and into your computer's USB port.
It will be detected as a virtual serial port that you can connect to with the
GNU Debugger (GDB). No middleman, no config scripts, no frustration. But it
seems that there are not very many people that know about it. Also unless you
are handy with a soldering iron and know what you are doing you will unlikely
end up using it for your hobby project.-->

<!--With 1Bitsy I decided to change the status quo. 1Bitsy is designed to work out
of the box with the Black Magic Probe JTAG/SWD debugger. The project is designed
to provide resources for you to get up and running quickly, with lot's of
examples, template projects, tutorials and software packages, that are designed
to be understood.-->

&mdash; Piotr Esden-Tempski (@esden)

## Next Steps

 * [Buy 1Bitsy](http://1bitsquared.com/products/1bitsy)
 * [Buy a Black Magic Probe](http://1bitsquared.com/products/black-magic-probe)
 * [Quick start](/overview/quickstart/)
 * [Join the Mailing List](/community/discourse-forum/)
 * [Star us on GitHub](https://github.com/1bitsy)
 * [Discussion Forum](http://discuss.1bitsy.org/)
