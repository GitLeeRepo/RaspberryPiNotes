# Overview

Assmebly Language notes for the Raspberry Pi ARM processor running the Raspbian Stretch OS

# References

## YouTube Videos

* [Assembly Language](https://www.youtube.com/watch?v=ViNnfoE56V8) - YouTube video series by Derek Banas on Raspberry Pi ARM assembly language

Examples

# Simple Program that sets return status and exits using a system call

```asm
.text

.global _start

_start:
        mov r0, #21        @ return value
        mov r7,#1          @ exit to terminal option
        swi 0              @ exit system call
```
