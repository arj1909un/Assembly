# Solve:
```
asm_bytes = asm("""
  b #0x40

nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop
nop

ldr x1, [sp]

mov x2, #0x3000
movk x2, #0x40, lsl #16
br x2
  """)
```
# Desc:
<img width="688" height="396" alt="i fee she totive" src="https://github.com/user-attachments/assets/cafb7e90-2cd2-4ed3-a480-d81c7b4cc787" />

b means relative offset which means move by 0x40 bytes from starting location.
br reg means branch to reg.
