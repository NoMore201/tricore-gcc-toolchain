# Changelog

## 13.4.1

### Upstream fixes and improvements

- [tricore-gcc] libatomic: Tricore support
- [tricore-gcc] Fix for libstdc++ atomic support
- [tricore-binutils-gdb] Fixing the location of the .gcc_except_table section in the default linker script

### Toolchain changes

- [tricore-gcc] tricore: use DECL_MD_FUNCTION_CODE for MD builtins and add
  bounds asserts
- Change version naming. Now using `x.y.z` where `x.y` is the current upstream
  gcc release, while `z` represents tricore specific versioning
- Fix build under WSL2
- Build with custom pkgversion to differentiate between upstream releases
- Update changelog

## 13.4-20250801

### Upstream fixes and improvements

- Fix an ICE related to LRA (resolve #9).
- FIX: Callinfo data structures need a dynamic allocation strategy
- Added support for TC4Zx device
- Fixed missing function from libgcc when soft-float is enabled
- Added mforce-align-arrays to make forced arrays alignmen optional
- Fixed wrong error message shown with --target-help
- Added support for TC46xx family
- Added memory mappings for tc4Dxx, tc48xx, tc46xx, tc45xx
- Added support to TC48xx family
- Added support for TC45xx family
- Added flag to disable hardware floating point instructions 
- Added tc49xx option for mcpu

### Toolchain changes

- Rebase tricore-gcc to version 13.4

## 13.3-20250516

- Rebase tricore-gcc to version 13.3
- Improvements to build flags, targets and release process

## 11.3.1-20250101

- Enable GDB build in tricore-binutils-gdb
- Merge GDB patches from go2sh/tricore-binutils-gdb
- Add material mkdocs docs with github actions trigger
- Fix LD crash in tricore-binutils-gdb
- Fix static build of GDB requiring external dependencies

## 11.3.1-20241211

- toolchain: Added QEMU 9.2.0 static executable to the toolchain, compiled with
  tricore support enabled
- script: Switch build script to a GNU autoconf based solution, insipired by
  [RiscV toolchain repository](https://github.com/riscv-collab/riscv-gnu-toolchain)
- release: Switched from commit SHA based release number to date release number.
  From now on, all releases will be tagged as `11.3.1-<date>` to better recognize
  different versions

## 11.3.1-5e4ca74

- binutils: Rename padding data, check for null pointer when dereferencing
- script: Use -gdwarf-3 option for win32 build

## 11.3.1-258811c

- binutils: Fix issue in extended map table showing garbage
  data for memory sections
- gcc: Fix build for macOS
- gcc: Add support for Tricore TC33x family MCUs

## 11.3.1-6eca707

- binutils: Fix issue in LD linker that caused crashes with some linker scripts