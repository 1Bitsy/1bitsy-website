---
lastmod: 2016-09-27
date: 2016-09-04
linktitle: Quickstart
menu:
  main:
    parent: getting started
next: /overview/installing
prev: /overview/introduction
title: 1Bitsy Quickstart Guide
weight: 10
---

# Quickstart on the command line

It is ultra easy to get going with 1Bitsy and Black Magic Probe. You need only
minimal amounts of software.

* [gcc-arm-embedded toolchain](https://launchpad.net/gcc-arm-embedded)
* [libopencm3](https://github.com/libopencm3/libopencm3)
* [some firmware code to play with](https://github.com/1BitSy/1bitsy-examples)

# Quickstart on Ubuntu GNU/Linux using [Black Magic Probe](http://github.com/blacksphere/blackmagic)

1: Add gcc-arm-embedded PPA and install the gcc-arm-embedded package
```
sudo add-apt-repository ppa:team-gcc-arm-embedded/ppa
sudo apt-get update
sudo apt-get install gcc-arm-embedded
```
2: Clone the 1Bitsy examples repository (you need to have git installed, if you don't have it run `sudo apt-get install git`)
```
git clone https://github.com/1Bitsy/1bitsy-examples.git
```
3: Build examples
```
cd 1bitsy-examples
git submodule init
git submodule update
make
```

4: Connect Black Magic Probe and your 1Bitsy to the computer. Also connect the
Black Magic Probe to your 1Bitsy using the JTAG ribbon cable. Make sure that you
plug in the Black Magic Probe first so that it's virtual serial interfaces get
indexed first. You can use the `dmesg` command to inspect what your linux kernel
is finding and doing while you are connecting thisgs together. Your 1Bitsy might
already have some firmware that exposes a serial port, which will interfere with
the instructions below. So make sure that your Black Magic Probe got
/dev/ttyACM0 and /dew/ttyACM1 assigned and not some other number. Of course you
can adjust the commands further down in case the device files have different
names.

5: Go to the example folder of your choosing and connect to Black Magic Probe using the arm-none-eabi GDB.
```
cd examples/1bitsy/fancyblink
arm-none-eabi-gdb fancyblink.elf
target extended_remote /dev/ttyACM0
monitor version
```
You should get information about the Black Magic Probe's firmware version.

6: Find and attach to the 1Bitsy using JTAG
```
monitor jtag_scan
attach 1
```
jtag_scan should list that it found the STM32F4 of the 1Bitsy and you should be
able to attach to it.

7: Upload and run the fanciblink example
```
load
run
```
you should now be running the fancyblink example. You can interrupt the
execution with Ctrl-C. You can now use all the GDB commands to inspect and step
through the firmware. For a detailed description of the functions see
appropriate tutorials.

8: Exit GDB. Just press Ctrl-C and Ctrl-D or type `exit`

The above steps 5-8 can also be accomplished by running `make flash`. But we
think it is nicer to actually see what is happening in the background so that
you have full control. :D

# Quickstart using PlatformIO

We are working on a self contained download of PlatformIO that is pre configured
for the use with the 1Bitsy platform. If you are interested in testing or helping with the development of this solution join us in our <a href="http://gitter.im/1bitsy/Lobby" target="_blank">Gitter Channel</a>.
