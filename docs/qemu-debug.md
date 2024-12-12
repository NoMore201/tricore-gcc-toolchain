# Debugging with QEMU

> This page is work in progress

This toolchain provides `qemu-system-tricore` and `tricore-elf-gdb` executable
that can be used to run and debug your code in a simulated environment.

> [!IMPORTANT]
> QEMU support for Tricore architecture is incomplete. It provides only basic
> CPU instruction decode (no interrupts or multi-core) and no peripheral is
> available. Only core architecture from tc1.3 up to tc1.6.2 is supported

TODO..