# Overview

Assmebly Language notes for the Raspberry Pi ARM processor running the Raspbian Stretch OS

Development here was done on a **Raspberry Pi 3** with an **BCM 2836 ARM v8** processor, which is an **SOC - System on a Chip** architecture.  It is a 1.2GHz chip with four ARM Cortex A53 cores.  It is a 64-bit processor, but it uses a 32-bit instruction set (for now anyway)

# References

## Books

* [Raspberry Pi Assembly Language RASPBIAN Beginners: Hands On Guide](https://www.amazon.com/Raspberry-Assembly-Language-RASPBIAN-Beginners/dp/1492135283/ref=sr_1_1?ie=UTF8&qid=1510393408&sr=8-1&keywords=raspberry+pi+assembly+language+raspbian+beginners)

## YouTube Videos

* [Assembly Language](https://www.youtube.com/watch?v=ViNnfoE56V8) - YouTube video series by Derek Banas on Raspberry Pi ARM assembly language

# Terminology and Concepts

* **#** - the hash sign is used to prefix an immediate value (a constant that is part of the instruction).  For example, **mov r7,#1**
* **@** - used to designate a comment in the source code
* **MSB** - Most Significant Bit - on a 32-bit ARM processor this is bit 31.  An overflow of this bit causes the **carry flag** to be set

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

# Data Types

Data Type | Bits | Bytes 
----------|------|-------
Byte      | 8    | 1
Word      | 32   | 4

# Examples

## Simple Program that sets return status and exits using a system call

```asm
.text

.global _start

_start:
        mov r0,#21         @ return value
        mov r7,#1          @ exit to terminal option
        swi 0              @ Raspbian exit system call
```
