# Description: 
Shifting bits around in assembly is another interesting concept!

x86 allows you to 'shift' bits around in a register.

Take, for instance, al, the lowest 8 (or least significant 8) bits of rax.

The value in al (in bits) is:

`al = 10001010`

If we shift once to the left using the shl instruction:

`shl al, 1`

The new value is:

`al = 00010100`

Everything shifted to the left, and the highest (or most significant) bit fell off while a new 0 was added to the right side.

You can use this to do special things to the bits you care about.

Shifting has the nice side effect of doing quick multiplication (by 2) or division (by 2), and can also be used to compute modulo.

Here are the important instructions:

shl reg1, reg2 <=> Shift reg1 left by the amount in reg2

shr reg1, reg2 <=> Shift reg1 right by the amount in reg2

Note: 'reg2' can be replaced by a constant or memory location.

When we say significant bit or least significant byte, significant means "most important for the value."

The least significant bit/byte carries the smallest weight (the "lowest" place value).

For example, when you modify the "lowest" or "rightmost" bit, the value changes just by 1.

The most significant bit/byte carries the highest weight (the "highest" place value).

For this challenge, using only the following instructions:

`mov, shr, shl`

Please perform the following: Set rax to the 5th least significant byte of rdi.

For example:

rdi = | B7 | B6 | B5 | B4 | B3 | B2 | B1 | B0 |

Set rax to the value of B4

# Solve:

```bash
   mov rax, rdi
     shr rax, 32
     shl rax, 56
     shr rax, 56
```
now our main aim to solve this is by removing all other bytes and make sure B4 is the only byte remaining

1. ` mov rax, rdi`
   so this was standard code nothing fancy we did this because we wanted to st the value of rax to b4
2. `shr rax, 32`
   getting rid of bytes 4,3,2,1 and 0 and b4 now becomes the least significant byte.
3. `shl rax, 56`
   getting rid of bytes 5,6,7 B4 becomes msb.
4. `shr rax, 56`
   moving b4 to lsb so we can get the exact int value of b4 .

