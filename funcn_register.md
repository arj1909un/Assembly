# Description:
Using your new knowledge, please compute the following:

f(x) = mx + b, where:

1. m = rdi
2. x = rsi
3. b = rdx

Place the result into rax.

Note: There is an important difference between mul (unsigned multiply) and imul (signed multiply) in terms of which registers are used. Look at the documentation on these instructions to see the difference.

In this case, you will want to use imul.

# Solve:
```bash
.intel_syntax noprefix
.global _start

_start:
    add rax, rdx
    imul rdi, rsi
    add rax, rdi
```

pretty self explanatory
