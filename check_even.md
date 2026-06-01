# Description :

In this level, you will be working with registers. You will be asked to modify or read from registers.

We will set some values in memory dynamically before each run. On each run, the values will change. This means you will need to perform some type of formulaic operation with registers. We will tell you which registers are set beforehand and where you should put the result. In most cases, it is rax.

In this level, you will be working with bit logic and operations. This will involve heavy use of directly interacting with bits stored in a register or memory location. You will also likely need to make use of the logic instructions in x86: and, or, xor.

Using only the following instructions:

* and
* or
* xor
  
Implement the following logic:

if x is even then
  y = 1
else
  y = 0
  
Where:
* x = rdi
* y = rax

# Solve :

```bash
and rdi, 1
xor rdi, 1
xor rax, rax
or  rax, rdi
```
1. `and rdi, 1`
   This keeps only the last bit of rdi, after this instruction rdi = 0 if og no. was even and rdi = 1 if og no. is 1.

2. `xor rdi, 1`
   this step flips the bit , so if rdi = 0 it becomes 1 and vice versa we did this beacuse the problem asked us to do it the other way around.

3. `xor rax, rax`
   step is done just to make sure rax has value as 0.

4. `or  rax, rdi`
   another way to write rax = rdi, as rax = 0 so or with 0 is the bit itself thus the use of or.
   
