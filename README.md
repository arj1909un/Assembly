# Setup:

To create an assembly source file use the following commands:

`nano solve.s`

after typing this command you will see something like this
```bash
.intel_syntax noprefix
.global _start

_start:
```
after typing the respective code run these commands to generate the flag.

```bash
as -o solve.o solve.s
ld -o solve solve.o
/challenge/run ./solve
```
