# Solve:
```

asm_bytes = asm("""
       mov  x2, x0
       mov  x0, #0
loop:
    ldr  x3, [x2], #8
    add  x0, x0, x3
    subs x1, x1, #1
    b.ne loop
  """)
```
# Desc:
Same as L11 but we need 6 instructions MAX
in this we remove the counter specific instruction and a new opcode SUBS which subtracts and sets flag in 1 clock cycle.
