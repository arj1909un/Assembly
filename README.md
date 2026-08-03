# Setup:

To create an assembly source file use the following commands:

`nano solve.s`

after typing this command you will see something like this
```bash
.intel_syntax noprefix
.global _start

_start:
```
we will breakdown this block of code to understand what's happening.

1. `intel_syntax noprefix`
By default, GNU assembler (as) expects AT&T syntax.
 But we know about intel syntax only:
   `mov rdi, 0x1337`
so this line tells assembler to interpret code as intel syntax

2. `.global _start
this is like a label for the entry point
after typing the respective code run these commands to generate the flag.

```bash
as -o solve.o solve.s
ld -o solve solve.o
/challenge/run ./solve
```
1. `as -o solve.o solve.s`
as → GNU assembler
solve.s → assembly source
 -o solve.o → output object file

converts human readable assembly into ,achine code object file(.o extension)

2. `ld -o solve solve.o`
 ld = linker
 solve.o = input object file
 -o solve = final executable name

creates elf structure
adds executable headers

## ELF : 
standard linux executable format
ELF contains:
* machine code
* memory layout info
* entry point
* sections like .text, .data

and /challenge/run is pwn native 
