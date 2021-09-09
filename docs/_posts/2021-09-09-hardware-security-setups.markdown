---
layout: post
title: "Hardware Security Setups"
date: 2021-09-09 11:39:30 +0900
categories: hardware security
---

# Research notes for hardware security

## Installing ARM development tools for Mac

{% highlight ruby %}
brew update
brew tap ArmMbed/homebrew-formulae
brew install arm-none-eabi-gcc
{% endhighlight %}

This will install the following tools.

{% highlight ruby %}
~/P/hardware-security-resaerch ❯❯❯ arm-none-eabi-                                                                                      ✘ 1
 -- external command --
arm-none-eabi-addr2line         arm-none-eabi-gcc               arm-none-eabi-gdb               arm-none-eabi-nm
arm-none-eabi-ar                arm-none-eabi-gcc-10.3.1        arm-none-eabi-gdb-add-index     arm-none-eabi-objcopy
arm-none-eabi-as                arm-none-eabi-gcc-ar            arm-none-eabi-gdb-add-index-py  arm-none-eabi-objdump
arm-none-eabi-c++               arm-none-eabi-gcc-nm            arm-none-eabi-gdb-py            arm-none-eabi-ranlib
arm-none-eabi-c++filt           arm-none-eabi-gcc-ranlib        arm-none-eabi-gprof             arm-none-eabi-readelf
arm-none-eabi-cpp               arm-none-eabi-gcov              arm-none-eabi-ld                arm-none-eabi-size
arm-none-eabi-elfedit           arm-none-eabi-gcov-dump         arm-none-eabi-ld.bfd            arm-none-eabi-strings
arm-none-eabi-g++               arm-none-eabi-gcov-tool         arm-none-eabi-lto-dump          arm-none-eabi-strip

{% endhighlight %}

## Install Segger j-link tools

1. Download the installer from [https://www.segger.com/downloads/jlink/](https://www.segger.com/downloads/jlink/)

2. Choose macOS (Intel or M1)

3. Install

If the installation is successful, an output like the following will be expected.

{% highlight ruby %}
~/P/hardware-security-resaerch ❯❯❯ JLinkExe - h
SEGGER J-Link Commander V7.54 (Compiled Sep  1 2021 10:42:02)
DLL version V7.54, compiled Sep  1 2021 10:41:55

Unknown command line option -h.
~/P/hardware-security-resaerch ❯❯❯
{% endhighlight %}


## Using J-Link Commander 

### Start Commander

See official documentation. [https://wiki.segger.com/J-Link_Commander](https://wiki.segger.com/J-Link_Commander)

{% highlight ruby %}
~/P/hardware-security-resaerch ❯❯❯ JLinkExe
SEGGER J-Link Commander V7.54 (Compiled Sep  1 2021 10:42:02)
DLL version V7.54, compiled Sep  1 2021 10:41:55

Connecting to J-Link via USB...Updating firmware:  J-Link EDU Mini V1 compiled Aug 10 2021 11:19:22
Replacing firmware: J-Link EDU Mini V1 compiled Jul 17 2020 16:25:21
Waiting for new firmware to boot
New firmware booted successfully
O.K.
Firmware: J-Link EDU Mini V1 compiled Aug 10 2021 11:19:22
Hardware version: V1.00
S/N: 801031379
License(s): FlashBP, GDB
VTref=0.000V


Type "connect" to establish a target connection, '?' for help
J-Link>
{% endhighlight %}


### Connect to Cortex-M4

![]({{site.baseurl}}/images/frdm-k64f.jpg)

{% highlight ruby %}
~/P/hardware-security-resaerch ❯❯❯ JLinkExe -device MK64FN1M0XXX12 -if SWD -speed 4000 -autoconnect 1 -CommanderScript download_flash.jlink
SEGGER J-Link Commander V7.54 (Compiled Sep  1 2021 10:42:02)
DLL version V7.54, compiled Sep  1 2021 10:41:55


J-Link Command File read successfully.
Processing script file...

J-Link connection not established yet but required for command.
Connecting to J-Link via USB...O.K.
Firmware: J-Link EDU Mini V1 compiled Aug 10 2021 11:19:22
Hardware version: V1.00
S/N: 801031379
License(s): FlashBP, GDB
VTref=3.299V
Target connection not established yet but required for command.
Device "MK64FN1M0XXX12" selected.


Connecting to target via SWD
InitTarget()
Found SW-DP with ID 0x2BA01477
DPIDR: 0x2BA01477
Scanning AP map to find all available APs
AP[2]: Stopped AP scan as end of AP map has been reached
AP[0]: AHB-AP (IDR: 0x24770011)
AP[1]: JTAG-AP (IDR: 0x001C0000)
Iterating through AP map to find AHB-AP to use
AP[0]: Core found
AP[0]: AHB-AP ROM base: 0xE00FF000
CPUID register: 0x410FC241. Implementer code: 0x41 (ARM)
Found Cortex-M4 r0p1, Little endian.
FPUnit: 6 code (BP) slots and 2 literal slots
CoreSight components:
ROMTbl[0] @ E00FF000
ROMTbl[0][0]: E000E000, CID: B105E00D, PID: 000BB00C SCS-M7
ROMTbl[0][1]: E0001000, CID: B105E00D, PID: 003BB002 DWT
ROMTbl[0][2]: E0002000, CID: B105E00D, PID: 002BB003 FPB
ROMTbl[0][3]: E0000000, CID: B105E00D, PID: 003BB001 ITM
ROMTbl[0][4]: E0040000, CID: B105900D, PID: 000BB9A1 TPIU
ROMTbl[0][5]: E0041000, CID: B105900D, PID: 000BB925 ETM
ROMTbl[0][6]: E0042000, CID: B105900D, PID: 003BB907 ETB
ROMTbl[0][7]: E0043000, CID: B105900D, PID: 001BB908 CSTF
Cortex-M4 identified.
Reset delay: 0 ms
Reset type NORMAL: Resets core & peripherals via SYSRESETREQ & VECTRESET bit.
Reset: Halt core after reset via DEMCR.VC_CORERESET.
Reset: Reset device via AIRCR.SYSRESETREQ.
AfterResetTarget()

No address passed for .bin file. Assuming address: 0x0
Downloading file [program.bin]...
Failed to open file.


Script processing completed.

~/P/hardware-security-resaerch ❯❯❯
{% endhighlight %}

For additional information about FRDM-k64f with J-Link, refer to [https://www.segger.com/evaluate-our-software/nxp/nxp-frdm-k64f/](https://www.segger.com/evaluate-our-software/nxp/nxp-frdm-k64f/)


## Installing OpenOCD

{% highlight ruby %}
brew install openocd
{% endhighlight %}

Detailed user's guide for OpenOCD is [https://openocd.org/doc/html/index.html](https://openocd.org/doc/html/index.html)


