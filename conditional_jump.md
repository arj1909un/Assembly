# Description:
<img width="1085" height="705" alt="image" src="https://github.com/user-attachments/assets/b45a5ab2-9741-48a8-99ca-9406881cbaa3" />
<img width="1094" height="632" alt="image" src="https://github.com/user-attachments/assets/20e47882-7aeb-43c5-a29e-7927fbf92ede" />

# Solve:
```bash
_start:
      cmp dword ptr [rdi], 0x7f454c46
je add_case

cmp dword ptr [rdi], 0x00005A4D
je sub_case

mov eax, [rdi+4]
imul eax, [rdi+8]
imul eax,  [rdi+12]
jmp done

add_case:
mov eax, [rdi+4]
add eax, [rdi+8]
add eax, [rdi+12]
jmp done

sub_case:
mov eax, [rdi+4]
sub eax, [rdi+8]
sub eax, [rdi+12]

done:
```
* `dword ptr`  this keyword tells the assembler how many bytes to compare, dwrord = 4 bytes so it reads 4 bytes from the address of rdi.
* `[rdi+4]`  we have done this before but to refresh the concepts, what it basically does is add 4 to the value of rdi and treats the result as an address.

now while reading the code we notice that why did we not use dword ptr over here `mov eax, [rdi+4]` and the reason is:

eax aldready means 4 bytes so we dont need to tell the assembler to use 4bytes of the register using dword ptr.

  
