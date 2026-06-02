# Description :
Recall that registers in x86_64 are 64 bits wide, meaning they can store 64 bits. Similarly, each memory location can be treated as a 64-bit value. We refer to something that is 64 bits (8 bytes) as a quad word.

Here is the breakdown of the names of memory sizes:

* Quad Word = 8 Bytes = 64 bits
* Double Word = 4 bytes = 32 bits
* Word = 2 bytes = 16 bits
* Byte = 1 byte = 8 bits
  
In x86_64, you can access each of these sizes when dereferencing an address, just like using bigger or smaller register accesses:
<img width="848" height="119" alt="image" src="https://github.com/user-attachments/assets/ea0bb3c1-f0cb-4ff5-b1b0-5144474c0ac3" />

Remember that moving into al does not fully clear the upper bytes.

Please perform the following: Set rax to the byte at 0x404000.

# Solve :
```bash
mov al, [0x404000]
```
Its pretty easy just refer to the image attatched above.


