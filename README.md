# ELF loader

A small elf loader. It can load static and dynamically linked ELF EXEC and DYN (pie) binaries. The loader is PIE program that doesn't depend on libc and calls kernel services directly (z_syscall.c).

If the loader needs to load a dynamically linked ELF it places an interpreter (usually ld.so) and a requested binary into a memory and then calls the interpreter entry point.

The program entry is not `main`, is `z_entry` function.


## Build

Default build is for amd64:

```shell
$ make
``` 

Build for i386:

```shell
$ make ARCH=i386
```

Small build (exclude all messages and printf):

```shell
$ make SMALL=1
```

## Load binaries

Load ls:

```shell
$ ./loader /bin/ls
```

Load galculator:

```shell
$ ./loader /usr/bin/galculator
```

