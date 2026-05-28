# Description: 
Division in x86 is more special than in normal math. Math here is called integer math, meaning every value is a whole number.

As an example: 10 / 3 = 3 in integer math.

Why?

Because 3.33 is rounded down to an integer.

The relevant instructions for this level are:

mov rax, reg1
div reg2
Note: div is a special instruction that can divide a 128-bit dividend by a 64-bit divisor while storing both the quotient and the remainder, using only one register as an operand.

How does this complex div instruction work and operate on a 128-bit dividend (which is twice as large as a register)?

For the instruction div reg, the following happens:

rax = rdx:rax / reg
rdx = remainder
rdx:rax means that rdx will be the upper 64-bits of the 128-bit dividend and rax will be the lower 64-bits of the 128-bit dividend.

You must be careful about what is in rdx and rax before you call div.

Please compute the following:

speed = distance / time, where:
distance = rdi
time = rsi
speed = rax
Note that distance will be at most a 64-bit value, so rdx should be 0 when dividing.

# Solve: 

```bash
.intel_syntax noprefix
.global _start

_start:
    mov rdx, 0x0
    mov rax, rdi
    div rsi
```

so we set rdx to 0 as we are using only 64bit dividend and then the rest is self explanatory.
