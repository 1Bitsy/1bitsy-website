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

{{< youtube ANM0fdAqDow >}}

## Quickstart on Ubuntu GNU/Linux using [Black Magic Probe](http://github.com/blacksphere/blackmagic)

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

5: Make sure your user is in the group `dialout`. You can see what groups your
user belongs to by typing the command `id`. If the group `dialout` is not listed
you can add yourself to the group:
```
sudo adduser $USER dialout
```

6: Go to the example folder of your choosing and connect to Black Magic Probe using the arm-none-eabi GDB.
```
cd examples/1bitsy/fancyblink
arm-none-eabi-gdb fancyblink.elf
target extended-remote /dev/ttyACM0
monitor version
```
You should get information about the Black Magic Probe's firmware version.

7: Find and attach to the 1Bitsy using JTAG
```
monitor jtag_scan
attach 1
```
jtag_scan should list that it found the STM32F4 of the 1Bitsy and you should be
able to attach to it.

8: Upload and run the fanciblink example
```
load
run
```
you should now be running the fancyblink example. You can interrupt the
execution with Ctrl-C. You can now use all the GDB commands to inspect and step
through the firmware. For a detailed description of the functions see
appropriate tutorials.

9: Exit GDB. Just press Ctrl-C and Ctrl-D or type `exit`

The above steps 5-8 can also be accomplished by running `make flash`. But we
think it is nicer to actually see what is happening in the background so that
you have full control. :D

## Quickstart on MacOS using [Black Magic Probe](http://github.com/blacksphere/blackmagic)

This instructions are almost exactly the same as for GNU/Linux with the exception
of the toolchain installation process and naming of the virtual serial ports.

Pre-requisites: [GIT](https://git-scm.com/). You can install GIT in many ways
but it has to be available in your Terminal.app. Meaning the $PATH variable has
to contain the place where your GIT binary is installed. You can check if your
system can find GIT by running `which git` it should list the path of it's
location.

1: Download [gcc-arm-embedded toolchain](https://launchpad.net/gcc-arm-embedded)
archive for MacOS.

2: Extract the archive in your home directory, and add the path to your shell
startup file:

```
cd ~
tar xfvj ~/Downloads/gcc-arm-none-eabi-XXX-mac.tar.bz2
echo 'export PATH=~/gcc-arm-none-eabi-XXX/bin:$PATH' >> .profile
export PATH=~/gcc-arm-none-eabi-XXX/bin:$PATH
```

Note: `XXX` is a placeholder that you have to replace with the version of the toolchain
that you are installing.

3: Make sure the gcc and gdb can be found:
```
which arm-none-eabi-gcc
which arm-none-eabi-gdb
```

Both commands should result in the path you added to your `PATH` environment
variable.

Clone the 1Bitsy examples repository (you need to have git installed, if you don't have it run `sudo apt-get install git`)
```
git clone https://github.com/1Bitsy/1bitsy-examples.git
```

4: Build examples
```
cd 1bitsy-examples
git submodule init
git submodule update
make
```

5: Connect Black Magic Probe and your 1Bitsy to the computer. Also connect the
Black Magic Probe to your 1Bitsy using the JTAG ribbon cable. You can look in
`About This Mac`->`System Report...`->`USB` if it is listing
`Black Magic Probe`, to make sure everything works the way it is supposed to.
You should list the virtual serial devices before and after you plug in BMP and
1Bitsy:
```
ls /dev/cu.usbmodem*
```

If the 1Bitsy has already some firmware that exposes a virtual serial port you will
see listings like the following:
```
/dev/cu.usbmodemXXX1
```

The Black Magic Probe serial ports will be listed as:
```
/dev/cu.usbmodemXXXXXXX1
/dev/cu.usbmodemXXXXXXX3
```

Where the `XXXXXXX` will be a combination of numbers and letters representing
the unique hardware identifier of your BMP.

6: Go to the example folder of your choosing and connect to Black Magic Probe
using the arm-none-eabi GDB.
```
cd examples/1bitsy/fancyblink
arm-none-eabi-gdb fancyblink.elf
target extended-remote /dev/cu.usbmodemXXXXXXX1
monitor version
```
You should get information about the Black Magic Probe's firmware version.

7: Find and attach to the 1Bitsy using JTAG
```
monitor jtag_scan
attach 1
```
jtag_scan should list that it found the STM32F4 of the 1Bitsy and you should be
able to attach to it.

8: Upload and run the fanciblink example
```
load
run
```
you should now be running the fancyblink example. You can interrupt the
execution with Ctrl-C. You can now use all the GDB commands to inspect and step
through the firmware. For a detailed description of the functions see
appropriate tutorials.

9: Exit GDB. Just press Ctrl-C and Ctrl-D or type `exit`

The above steps 5-8 can also be accomplished by running
`make flash BMP_PORT=/dev/cu.usbmodemXXXXXXX1`. But we think it is nicer to
actually see what is happening in the background so that you have full control.
:D

## Quickstart on Windows using [Black Magic Probe](http://github.com/blacksphere/blackmagic)

TODO!~ If you are a Windows user and want to contribute a Quick Start Guide
join the Gitter channel in the lower right corner of this page, and let us know.

The main difference will be how to install the toolchain and get a command line.
CygWin is probably one of the ways to do that. Also you will need a [codeless
driver](http://www.blacksphere.co.nz/downloads/driver.w32.zip). The driver is
unsigned so you will need to convince your Windows 10 to accept it. Also the
driver does not contain any code so it should work on Windows 32 and 64. If it
does not, let us know how to fix this. :)

## Quickstart on Linux using DFU Bootloader

This solution is very simple and will allow you to upload a firmware to your
1Bitsy. This solution does not provide any debugging capabilities. Refer to the
[Black Magic Probe](http://github.com/blacksphere/blackmagic) guides if you
want to be able to inspect your programs.

DFU stands for Device Firmware Upgrade. It is a generic USB mode allowing
firmware upload to embedded devices.

Pre-requisites: You need to have GIT and dfu-util installed. Make sure that
the dfu-util is at least version 0.8.

1: Add gcc-arm-embedded PPA and install the gcc-arm-embedded package
```
sudo add-apt-repository ppa:team-gcc-arm-embedded/ppa
sudo apt-get update
sudo apt-get install gcc-arm-embedded
```
2: Clone the 1Bitsy examples repository (you need to have git installed, if you
don't have it run `sudo apt-get install git`)
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

4: Launch the factory provided built in DFU bootloader.

There are two ways you can enter the built in factory DFU bootloader on the
1Bitsy. By default all 1Bitsy that you can purchase from
[1BitSquared](https://1bitsquared.com/collections/embedded-hardware) come pre
loaded with a firmware that will launch the built in bootloader if you plug in
the 1Bitsy USB port into your computer while holding down the "User" button.

All examples found in the
[1bitsy-examples](https://github.com/1bitsy/1bitsy-examples) repository have
the same behavior as above.

You can inspect if you see an STM32 bootloader when listing your USB devices with
the `lsusb` command.

The alternative is to short the `BOOT` pads on the back of your 1Bitsy, either
with a solder blob or tweezers. While those pads are shorted the bootloader
will be launched as soon as you plug in your 1Bitsy over USB in to your
computer.

Note: The factory bootloader also supports other interfaces than USB. With the
correct tools you can also upload firmware over serial, i2c, CAN and SPI. In
some cases if you want to launch the built in bootloader and have some hardware
connected to the other available interfaces provided by the bootloader it
happens that the bootloader locks onto one of the other interfaces and not the
USB interface. So if you have trouble launching the DFU bootloader make sure to
disconnect all the external connections you might have.

5: Upload a binary to your 1Bitsy.

```
cd examples/1bitsy/fancyblink
make fancyblink.bin
sudo dfu-util -d 0483:df11 -c 1 -a 0 -s 0x08000000:leave -D fancyblink.bin
```

# Quickstart using PlatformIO

We are working on a self contained download of PlatformIO that is pre configured
for the use with the 1Bitsy platform. If you are interested in testing or helping with the development of this solution join us in our <a href="http://gitter.im/1bitsy/Lobby" target="_blank">Gitter Channel</a>.
