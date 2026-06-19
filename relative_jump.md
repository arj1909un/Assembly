# Description:
<img width="1090" height="687" alt="image" src="https://github.com/user-attachments/assets/2a7faf2c-30d8-4bef-9566-8abe4dca356f" />

# Solve:
```bash
_start:
    jmp target

    .rept 81

    nop

    .endr

target:
      mov rax, 0x1
```
now in this chal we will notice the `target:` label.

A label is simply a name for a location in memory and allows us to jump to that location without knowing its exact address beforehand.

To ensure that target is located exactly 0x51 bytes after the jump instruction, padding bytes were inserted between the jump and the label using nop instructions. Since each nop occupies one byte, the number of nops determines the distance between the jump and the destination.

After testing, it was observed that the jump instruction occupied more bytes than initially expected. The challenge output indicated that the destination was two bytes short, meaning two additional bytes of padding were required. Increasing the padding by two nops placed the label at the correct offset.

