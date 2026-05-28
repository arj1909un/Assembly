# Description: 
x86 allows you to get the remainder after a div operation.

For instance: 10 / 3 results in a remainder of 1.

The remainder is the same as modulo, which is also called the "mod" operator.

In most programming languages, we refer to mod with the symbol %.

Please compute the following: rdi % rsi

Place the value in rax.

# Solve:

```bash
.intel_syntax noprefix
.global _start

_start:
      mov rdx, 0x0
      mov rax, rdi
      div rsi
      mov rax, rdx
```

so rdx gets the remainder after doing div rsi and we need to place it in rax so thus the extra line:
` mov rax, rdx`
