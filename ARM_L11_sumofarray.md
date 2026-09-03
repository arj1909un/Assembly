# Solve:
```
asm_bytes = asm("""
  mov x2, x0
  mov x0, #0
  mov x4, x1
  mov x1, #0
loop:

ldr x3,[x2]
add x0, x0, x3
add x2, x2, #8
add x1, x1, #1

cmp x1, x4
b.lt loop
  """)
```
# Desc:
Loops can be created using conditional branch instructions.
The branch instruction in aarch64 is b.
To conditionally branch a dot suffix (ex: .gt) is appended resulting in b.gt.
This would be equivalent to jg in amd64.


Please compute the sum of n consecutive quad words, where:
        X0 = memory address of the 1st quad word
        X1 = n (amount to loop for)

set x0 to the sum computed

We will now set the following in preparation for your code:
        - [0x4042c0:0x404460] = {n qwords]}
        - X0 = 0x4042c0
        - X1 = 52

Please give me your assembly in bytes (up to 0x1000 bytes):
