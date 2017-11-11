# Overview

Assmebly Language notes for the Raspberry Pi ARM processor running the Raspbian Stretch OS

# References

## Books

* [Raspberry Pi Assembly Language RASPBIAN Beginners: Hands On Guide](http://tinyurl.com/y9tpnz5q)

## YouTube Videos

* [Assembly Language](https://www.youtube.com/watch?v=ViNnfoE56V8) - YouTube video series by Derek Banas on Raspberry Pi ARM assembly language

# Assemble and Link Commands

## Assemble

```bash
as -o progname.o progname.s
```

## Link Single File

```bash
ld -o progname progname.o
```

## Link Multiple Object files 

Assuming two separate source files assebled to two different object files

```bash
ld -o progname prognmain.o progmodule.o
```

# Examples

## Simple Program that sets return status and exits using a system call

```asm
.text

.global _start

_start:
        mov r0,#21         @ return value
        mov r7,#1          @ exit to terminal option
        swi 0              @ exit system call
```
