# Description :
In this level, you will be working with memory. This will require you to read or write to things stored linearly in memory. If you are confused, go look at the linear addressing module in 'ike. You may also be asked to dereference things, possibly multiple times, to things we dynamically put in memory for your use.

It is worth noting, as you may have noticed, that values are stored in reverse order of how we represent them.

As an example, say:

[0x1330] = 0x00000000deadc0de

If you examined how it actually looked in memory, you would see:

* [0x1330] = 0xde
* [0x1331] = 0xc0
* [0x1332] = 0xad
* [0x1333] = 0xde
* [0x1334] = 0x00
* [0x1335] = 0x00
* [0x1336] = 0x00
* [0x1337] = 0x00
  
This format of storing things in 'reverse' is intentional in x86, and it's called "Little Endian".

For this challenge, we will give you two addresses created dynamically each run.

The first address will be placed in rdi. The second will be placed in rsi.

Using the earlier mentioned info, perform the following:

-> Set [rdi] = 0xdeadbeef00001337

-> Set [rsi] = 0xc0ffee0000

Hint: it may require some tricks to assign a big constant to a dereferenced register. Try setting a register to the constant value, then assigning that register to the dereferenced register.

# Solve:
```bash
mov rax, 0xdeadbeef00001337
mov [rdi], rax


mov rax, 0xc0ffee0000
mov [rsi], rax
```

now the question arises why cant we directly assign value to the derefferenced register bcuz on x86-64, you cannot directly move an arbitrary 64-bit immediate value into memory with a single mov instruction.

so we do it in 2 steps

`mov rax, 0xdeadbeef00001337`

This is allowed because:

1. mov rax, imm64 can load a 64-bit constant into a register.
2. mov [rdi], rax can store a 64-bit register into memory.

Think of it as:
* Big constant → Register → Memory


Rather than:
* Big constant → Memory

For smaller constants, direct stores are often allowed:

`mov dword ptr [rdi], 1234`

because 1234 fits in 32 bits.
