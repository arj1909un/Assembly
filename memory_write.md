# Description:
n this level, you will be working with memory. This will require you to read or write to things stored linearly in memory. If you are confused, go look at the linear addressing module in 'ike. You may also be asked to dereference things, possibly multiple times, to things we dynamically put in memory for your use.

Please perform the following: Place the value stored in rax to 0x404000.

# Solve:

```bash
mov [0x404000], rax
```
now while solving i tried this first

`mov 0x40400, rax`

 now we cant work with this as it shows an operand mismatch becuz oth operands can’t be memory locations (no bracket = value).

 x86 sees 0x40400 as a memory address, so this means thus(bracket = memory address):
 `mov [0x404000], rax`
 

 
