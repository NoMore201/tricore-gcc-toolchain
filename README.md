
# Tricore GCC

## Building (cross-compile)

This chapter refers to cross-compiling from host architecture to `tricore-elf`
target. In this scenario, build architecture is the same as the host 
architecture.

Instructions showed here are tested on Ubuntu 22.04 (see
[Github Actions script](./.github/workflows/build.yml)), but should ideally
work on other Linux distributions and also MSYS2 Windows environment.

Clone the repository:

```sh
git clone --recursive git@github.com:EEESlab/tricore-gcc-toolchain-11.3.0.git
```

Install build dependencies:

```sh
sudo apt-get update
sudo apt-get -y install build-essential texinfo \
    flex bison libmpfr-dev libgmp-dev libmpc-dev zip libdebuginfod-dev
```

Create a temporary build directory and call the `configure` script

```sh
mkdir build && cd build
../configure --prefix=/path/to/prefix
make -j$(nproc)
```

This will build and install everything into `/path/to/prefix`.

It is also possible to compile single components of the toolchain. For further information on the available options, refer to `configure` script help page and
the [Makefile](./Makefile.in).

## Building (canadian-cross)

Sometimes it may be useful to build a cross-compiler from architecture B to architecture C, by performing the build on a third architecture A. The reason
is that setting up architecture B for cross-compilation may be not as easy as
on architecture A. This is called a 
[canadian cross](https://en.wikipedia.org/wiki/Cross_compiler#Canadian_Cross).

In this case, the idea is to build Win32 tricore-elf-gcc (cross-compiler from
Win32 to `tricore-elf`) directly on Linux due to easier setup and the 
reproducibility of the environment.

Canadian cross build is performed by the
[Github Actions script](./.github/workflows/build.yml). First clone the
toolchain repository:

```sh
git clone --recursive git@github.com:EEESlab/tricore-gcc-toolchain-11.3.0.git
```

Install build dependencies, including MinGW cross-compiler:

```sh
sudo apt-get update
sudo apt-get -y install build-essential texinfo \
    flex bison libmpfr-dev libgmp-dev libmpc-dev zip libdebuginfod-dev \
    gcc-mingw-w64 g++-mingw-w64
```

First we need to build the linux -> tricore cross-compiler. Refer to the
[Build cross-compile section](#building-cross-compile) on how to do so.

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