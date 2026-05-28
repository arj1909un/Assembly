# Description:
It turns out that using the div operator to compute the modulo operation is slow!

We can use a math trick to optimize the modulo operator (%). Compilers use this trick a lot.

If we have x % y, and y is a power of 2, such as 2^n, the result will be the lower n bits of x.

Therefore, we can use the lower register byte access to efficiently implement modulo!

Using only the following instruction(s):

mov

Please compute the following:

rax = rdi % 256

rbx = rsi % 65536

# Solve: 

```bash
.intel_syntax noprefix
.global _start

_start:
    mov al, dil
    mov bx, si
```

now while using mov we have to make sure that both the registers are of same size

1. `mov al, dil`

* dil = lowest 8 bits of rdi
* al = lowest 8 bits of rax

2. `mov bx, si`

* si = lowest 16 bits of rsi
* bx = lowest 16 bits of rbx

so the important thing is to make sure you are using the right bits for that certain register.

