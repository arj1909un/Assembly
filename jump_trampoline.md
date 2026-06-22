# Description:
<img width="1107" height="451" alt="image" src="https://github.com/user-attachments/assets/73a900c7-b296-4742-b9f0-4250396c4769" />

# Solve:
```bash
_start:
    jmp target

    .rept 81

    nop

    .endr

target:
      pop rdi
      mov rax, 0x403000
      jmp rax
```
just follow the instructions and refer the previous challenges to solve.
