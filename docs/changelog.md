# Changelog

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