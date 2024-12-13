
# Tricore GNU compiler toolchain

![ci build status](https://github.com/NoMore201/tricore-gcc-toolchain/actions/workflows/build.yml/badge.svg)

C/C++ toolchain based on GCC 11.3 for AURIX Tricore architecture. It supports
TriCore architectures 1.3, 1.3.1, 1.6, 1.6.1, 1.6.2 and 1.8. Currently it
includes the following software:

- GCC 11.3.1
- Binutils 2.40
- libc based on Cygwin Newlib
- QEMU 9.2.0  with Tricore support
- GDB 14.0 with Tricore support

Documentation is published through Github Pages in [Docs](https://nomore201.github.io/tricore-gcc-toolchain/)

> This repository is a downstream of
> [EEESlab/tricore-gcc-toolchain-11.3.0](https://github.com/EEESlab/tricore-gcc-toolchain-11.3.0)
> that aims to be a playground for new features and improvements with a faster
> developement process and automated release management. All the meaningful
> changes will be contributed back to upstream repository

## Download pre-built toolchain packages

Prebuilt packages are available in the
[release section](https://github.com/NoMore201/tricore-gcc-toolchain/releases).

## Building

Please refer to [docs/building.md](./docs/building.md) document for build
instructions.