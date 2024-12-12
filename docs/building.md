# Build instructions

## GCC Toolchain

### Native build

This chapter refers to building the Tricore cross-compiler directly from the
host architecture.

Instructions showed here are tested on Ubuntu 22.04 (see
[Github Actions script](https://github.com/NoMore201/tricore-gcc-toolchain/blob/main/.github/workflows/build.yml)), but should ideally
work on other Linux distributions and also MSYS2 Windows environment.

Clone the repository:

```sh
git clone --recursive https://github.com/NoMore201/tricore-gcc-toolchain
```

Install build dependencies:

```sh
sudo ./scripts/install-apt-dependencies
```

Create a temporary build directory and call the `configure` script

```sh
mkdir build && cd build
../configure --prefix=/path/to/prefix
make -j$(nproc) stamps/build-gcc-stage2
```

This will build and install everything into `/path/to/prefix`.

It is also possible to compile single components of the toolchain. For further information on the available options, refer to `configure` script help page and
the [Makefile](https://github.com/NoMore201/tricore-gcc-toolchain/blob/main/Makefile.in).

### MinGW canadian cross build

Sometimes it may be useful to build a cross-compiler from architecture B to architecture C, by performing the build on a third architecture A. The reason
is that setting up architecture B for cross-compilation may be not as easy as
on architecture A. This is called a 
[canadian cross](https://en.wikipedia.org/wiki/Cross_compiler#Canadian_Cross).

In this case, the idea is to build Win32 tricore-elf-gcc (cross-compiler from
Win32 to `tricore-elf`) directly on Linux due to easier setup and the 
reproducibility of the environment.

You can see an example of a canadian cross build in the
[Github Actions script](https://github.com/NoMore201/tricore-gcc-toolchain/blob/main/.github/workflows/build.yml). First clone the
toolchain repository:

```sh
git clone --recursive https://github.com/NoMore201/tricore-gcc-toolchain
```

Install build dependencies, including MinGW cross-compiler:

```sh
sudo ./scripts/install-apt-dependencies
```

First we need to build the linux -> tricore cross-compiler. Refer to the
[Native build](#native-build) chapter on how to do so.

When linux -> tricore cross-compiler is ready, we need to install the newlib
also into the final Win32 prefix. To do so, switch to the linux build directory
and call make by swapping the prefix variable:

```sh
cd build-linux/build-newlib
make install prefix=/path/to/win32-prefix
```

Now modify `PATH` environment variable with the PATH to linux cross-compiler:

```sh
export PATH="/path/to/linux-prefix:$PATH"
```

Finally we configure and build the missing components with the following
commands

```sh
mkdir build-win32 && cd build-win32
../configure --prefix /path/to/win32-prefix --with-host=x86_64-w64-mingw32
make -j$(nproc) stamps/build-binutils-tc
export PATH="/opt/gcc/linux/bin:$PATH"
make -j$(nproc) stamps/build-gcc-stage2-only
```

## QEMU

### Native build

> WIP

### MinGW canadian cross build

> WIP