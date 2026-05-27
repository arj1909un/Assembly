# Description:
For shorthand, when we say A += B, it really means A = A + B.

Here are some useful instructions:

<img width="393" height="103" alt="image" src="https://github.com/user-attachments/assets/f67419a3-030b-49b6-8281-848814df88fd" />


div is more complicated, and we will discuss it later. Note: all regX can be replaced by a constant or memory location.

Do the following:

Add 0x331337 to rdi

# Solve:
```bash
  GNU nano 8.7                                                   solve.s                                                             
.intel_syntax noprefix
.global _start

_start:
    add rdi, 0x331337
```
Now the interseting thing is that u cant give register a value it can only copy values so the code becomes a bit different
`add rdi, 0x331337`
now what this does is rdi += 0x331337, so rdi = rdi(original value that it had) + 0x331337

