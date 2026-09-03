# Solve:
```
asm_bytes = asm("""
  ldp x0, x1, [sp], #16
ldp x2, x3, [sp], #16
ldp x4, x5, [sp], #16
ldp x6, x7, [sp], #16

add x0, x0, x1
add x0, x0, x2
add x0, x0, x3
add x0, x0, x4
add x0, x0, x5
add x0, x0, x6
add x0, x0, x7

lsr x0, x0, #3

str x0, [sp, #-16]!
  """)
```
# Desc:
nstead, you must use ldr and str to retrieve values from the stack.
Fortunately, both ldr and str have the ability to increment the address passed in pre/post access.
This feature can be used to perform the same action!

popping the stack would be of the form:
        ldr x1, [sp], #16

This loads the value located at the stack pointer into register x1 and then adds 16 to the stack.

Pushing to the stack would be of the form
        str x1, [sp, #-16]!

This subtracts 16 from the stack pointer and then stores the value in x1 at sp.
Note: In aarch64, the stack pointer must be 16 byte aligned!  Accessing the stack pointer when it is
not properly aligned will result in a fault!

Note: There is different syntax for accessing memory at an offset, pre-indexing, and post-indexing.
All of these forms are used extensively in aarch64.

Please pop 8 QWORDS from the stack, compute their average, and push the result back onto the stack.
