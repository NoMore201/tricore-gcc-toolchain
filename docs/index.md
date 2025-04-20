# Tricore GNU toolchain

Free and open source cross-compiler toolchain for AURIX™ TriCore™
microcontrollers. It supports TriCore™ architecture from 1.3 up to 1.8 and
includes the following software:

- GCC 13.3
- Binutils 2.40
- libc based on Cygwin Newlib
- QEMU 9.2.0
- GDB 14.0 with Tricore support

> This repository is a downstream of
> [EEESlab/tricore-gcc-toolchain-11.3.0](https://github.com/EEESlab/tricore-gcc-toolchain-11.3.0)
> that aims to be a playground for new features and improvements with a faster
> developement process and automated release management. All the meaningful
> changes will be contributed back to upstream repository

## Download

Grab the latest pre-compiled toolchain from
[GitHub releases](https://github.com/NoMore201/tricore-gcc-toolchain/releases).

To build manually from sources, please refer to the [build page](./building.md).

## Code samples

- [AURIX_code_examples](https://github.com/Infineon/AURIX_code_examples):
collection of code samples from Infineon meant to be used with
AURIX™ Development Studio
- [aurix-cmake-code-sample](https://github.com/NoMore201/aurix-cmake-code-sample):
Project based on Blinky_LED_1_KIT_TC334_LK from Infineon repository
updated with CMake supports and modern tools (clang-format, clang-tidy)
