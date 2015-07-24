![Interim OS Bomberjacket Logo](http://dump.mntmn.com/bjos.png)

Interim
-------

Interim OS is a radical new operating system with a focus on minimalism. It steals conceptually from Lisp machines (language-based kernel) and Plan 9 (everything is a file system). It boots to a JITting Lisp-like REPL and offers the programmer/user the system's resources as filesystems.

Interim runs on:
- Raspberry Pi 2 (Broadcom VideoCore4/ARMv7, Bare Metal)
- Olimex Olinuxino (Freescale IMX233/ARMv5, Bare Metal)
- ARM5+ Linux (Hosted)
- Intel/AMD x64 Linux (Hosted)

Architecture
------------

- Layer 2: Bitmapped Terminal / Editor
- Layer 1: Sledge Lisp JIT Compiler
- Layer 0: Platform Interface (Startup code and filesystems)

![Interim OS Screenshot](http://dump.mntmn.com/interim-paper/illustrations/interim-picture.jpg)

Design Choices
--------------

- The shell is the editor is the REPL is the language is the compiler.
- Namespacing allows sandboxing and network transparency.
- You need only one text encoding: UTF-8.
- All facilities must be navigable by keyboard.

Building
--------

1. Get the dependencies. For a (Linux-)hosted version, this is only GCC and SDL1 or SDL2 if you want windowed graphics. Sledge can also use /dev/fb0 instead if available on your platform. If you want to cross-compile for an ARM platform, get *arm-none-eabi-gcc* and *libnewlib-arm-none-eabi*.

2. To build the hosted variant, cd to ````sledge```` and ````./build_x64.sh````.

3. To cross-compile for bare metal, use ````./rpi2-build.sh```` or ````./imx233-build.sh````.

Running (Hosted)
----------------

    cd sledge
    ./sledge

Running (Raspberry Pi 2)
------------------------

Prepare a bootable SD card with the usual FAT partition that has the Pi-specific boot blobs in it and copy ````kernel.img```` into it. You can recycle any other Raspberry OS distribution, i.e. Raspian for this. Just replace the kernel.img and delete cmdline.txt. Keyboard input is currently only over UART, so you will probably want to connect a UART->USB cable to another computer and use it to control Interim. 

Licenses
--------

Interim OS: GNU GPLv3 or later, (C) 2015 Lukas F. Hartmann / @mntmn

Interim OS is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.
This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

- newlib: GNU GPLv2, Maintained by Corinna Vinschen, Jeff Johnston / Red Hat Inc.
- devices/rpi2/uspi: GNU GPLv3, Copyright (C) 2014-2015  R. Stange <rsta2@o2online.de>
- devices/rpi2/rpi-boot: Copyright (C) 2013 by John Cronin <jncronin@tysos.org>
- GNU Unifont: GNU GPLv2+, originally by Roman Czyborra

Codecs

- minimp3: GNU LGPL, Copyright (C) 2001, 2002 Fabrice Bellard, (C) 2007 Martin J. Fiedler
- uPNG: zlib License, Copyright (C) 2005-2010 Lode Vandevenne, (C) 2010 Sean Middleditch
- NanoJPEG: KeyJ's Research License, Copyright (C) 2014 Martin J. Fiedler
