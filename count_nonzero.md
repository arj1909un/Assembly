# Description:
<img width="1197" height="754" alt="image" src="https://github.com/user-attachments/assets/96ee48ba-e8d0-4e18-8bb9-00502e34e24f" />

# Solve:
```bash
_start:
      mov rax, 0

    cmp rdi, 0
    je done

loop:
    cmp byte ptr [rdi + rax], 0
    je done
    inc rax
    jmp loop

done:
```
to understand what we have written I have written the code in C to fully understand whats going on.

```bash
long count_nonzero(char *rdi) {
    long rax = 0;
    if (rdi == 0) return 0;
    while (rdi[rax] != 0) {
        rax++;
    }
    return rax;
}
```
this helps us understand our problem statement.

* in the 1st line of our assembly code we are setting the value of rax as 0.

* then we compare the value of rdi with 0 and jump to the done label if true.

* in the loop label `[rdi + rax]` means "the memory address you get by adding rdi and rax" — exactly like `rdi[rax]` in C (pointer + index = array access). byte ptr tells the assembler "read just 1 byte from that address," since a register on its own doesn't say how many bytes to read. This compares that byte to 0.

* as soon as we find 0 in the array we jump out of the loop into the done label.

* the next few lines are easy to understand as we are using post increment on rax and then jumping out of the loop once the condition is met.


