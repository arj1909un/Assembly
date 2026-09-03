# solve:
```
#!/usr/bin/env python3
from pwn import *
context.arch = 'aarch64'

asm_bytes = asm("""
      mov  x0, #0x4000
movk x0, #0x40, lsl #16
ldp  x1, x2, [x0]
stp  x1, x2, [x0, #16]
  """)

with process('/challenge/run') as p:
  p.send(asm_bytes)
  p.stdin.close()
  p.interactive()
```
# desc :
Consecutive memory addresses can be loaded and stored in a single instruction as a pair!

Please perform the following:
        1. Place the value stored at 0x404000 to the memory location 0x404010
        2. Place the value stored at 0x404008 to the memory location 0x404018
Constraints:
        - You can only use mov, movk, stp, and ldp
        - You are allowed four instructions

We will now set the following in preparation for your code:
        [0x404000] = 0x128e39
        [0x404008] = 0x126b77
