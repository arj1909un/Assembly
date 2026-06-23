# Description:
<img width="1088" height="635" alt="image" src="https://github.com/user-attachments/assets/e434791a-622d-4b2d-b765-981d665cb745" />

# Solve:
```bash
_start:
    mov rax, 0          
    mov rcx, 0          

LOOP:
    cmp rcx, rsi
    jae DONE

    add rax, [rdi + rcx*8]
    inc rcx
    jmp LOOP

DONE:
    xor rdx, rdx
    div rsi
```
so in this challenge luckily for us we have all the numbers stored consecutively in rdi.

1. `mov rax, 0 ` and `mov rcx, 0` these statements set the count to zero for both the sum and loop counter.
2. `cmp rcx, rsi ` we compare i and n and as soon as i become greater than n, we stop the loop and jmp to done.
3. `add rax, [rdi + rcx*8]` just the sum condition.
4. `inc rcx` just increases the loop counter.

main focus on the `DONE` label 

* ` xor rdx, rdx` this line is just to set rdx to 0 so that `div rsi` just becomes `rax/rsi`.
  

