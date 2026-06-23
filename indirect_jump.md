# Description:
The last jump type is the indirect jump, often used for switch statements in the real world. Switch statements are a special case of if-statements that use only numbers to determine where the control flow will go.

Here is an example:
```
switch(number):
  0: jmp do_thing_0
  1: jmp do_thing_1
  2: jmp do_thing_2
  default: jmp do_default_thing
```
The switch in this example works on number, which can either be 0, 1, or 2. If number is not one of those numbers, the default triggers. You can consider this a reduced else-if type structure. In x86, you are already used to using numbers, so it should be no surprise that you can make if statements based on something being an exact number. Additionally, if you know the range of the numbers, a switch statement works very well.

Take, for instance, the existence of a jump table. A jump table is a contiguous section of memory that holds addresses of places to jump.

In the above example, the jump table could look like:
```
[0x1337] = address of do_thing_0
[0x1337+0x8] = address of do_thing_1
[0x1337+0x10] = address of do_thing_2
[0x1337+0x18] = address of do_default_thing
```
Using the jump table, we can greatly reduce the amount of cmps we use. Now all we need to check is if number is greater than 2. If it is, always do:

`jmp [0x1337+0x18]`

Otherwise:

`jmp [jump_table_address + number * 8]`

Using the above knowledge, implement the following logic:
```
if rdi is 0:
  jmp 0x40301e
else if rdi is 1:
  jmp 0x4030da
else if rdi is 2:
  jmp 0x4031d5
else if rdi is 3:
  jmp 0x403268
else:
  jmp 0x40332c
```
Please do the above with the following constraints:

* Assume rdi will NOT be negative.
* Use no more than 1 cmp instruction.
* Use no more than 3 jumps (of any variant).
* We will provide you with the number to 'switch' on in rdi.
* We will provide you with a jump table base address in rsi.
  
 Here is an example table:
  
```
[0x40427c] = 0x40301e (addrs will change)
[0x404284] = 0x4030da
[0x40428c] = 0x4031d5
[0x404294] = 0x403268
[0x40429c] = 0x40332c
```

# Solve:

```bash
_start:
      cmp rdi, 3
ja  default

jmp qword ptr [rsi + rdi*8]

default:
jmp qword ptr [rsi + 4*8]
```

we are executing a jump table that we do when we want to replicate the use of switch statement.

1. `cmp rdi, 3`  what this statement basically does is check if ` rdi > 3` if yes then it jumps to the default case.
2. `jmp qword ptr [rsi + rdi*8]`  means:

```
   base = rsi
index = rdi
element size = 8 bytes
contents used as jump target

therefore:
array of addresses (jump table)
```
the crux of the code being there is a jump table which contains the addresses of all the locations we would have jumped to if we would have satisfied the if statement thus this line of code.

3. `jmp qword ptr [rsi + 4*8]`  now this statement has more to do with the jump table if you see the addresses in the table you realise the last address value is for the default case because there is no other value in the if statement that belongs to that address.

   
