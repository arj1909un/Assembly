# Description:
Please perform the following:

* Place the value stored at 0x404000 into rax.
* Increment the value stored at the address 0x404000 by 0x1337.

Make sure the value in rax is the original value stored at 0x404000 and make sure that [0x404000] now has the incremented value.

# Solve:

```bash
       mov rax, [0x404000]
       add qword ptr [0x404000], 0x1337
```
first line is pretty self explanatory.

2. `add qword ptr [0x404000], 0x1337`
   
 means:
* Go to address 0x404000.
* Read the 8-byte value stored there.
* Add 0x1337 to it.
* Store the result back at 0x404000
  
