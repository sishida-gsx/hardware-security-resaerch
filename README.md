# Research notes for hardware security

## Installing ARM development tools for Mac

```
brew update
brew tap ArmMbed/homebrew-formulae
brew install arm-none-eabi-gcc
```

This will install the following tools.

```
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

```

## Install Segger j-link tools

1. Download the installer from [https://www.segger.com/downloads/jlink/](https://www.segger.com/downloads/jlink/)

2. Choose macOS (Intel or M1)

3. Install

If the installation is successful, an output like the following will be expected.

```
~/P/hardware-security-resaerch ❯❯❯ JLinkExe -h                                                                                       ✘ 126
SEGGER J-Link Commander V7.54 (Compiled Sep  1 2021 10:42:02)
DLL version V7.54, compiled Sep  1 2021 10:41:55

Unknown command line option -h.
~/P/hardware-security-resaerch ❯❯❯
```
