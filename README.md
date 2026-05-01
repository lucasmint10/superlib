# superlib
A libray that has all of the operations in a CPU.

Bundles every operation in a single libray for use.

# Example
```assembly
.data
  lname db "superlib.exe", 0

.code
start:
   push offset lname
   call LoadLibraryA
   test eax, eax
   jz fail
   add eax, 0x1003
   push 1
   push 1
   call eax
   jmp success

success:
    xor eax, eax
    ret
   
fail:
    mov eax, 0xFFFFFFFF
    ret
```

# Usage
```
-- superlib.exe FUNCTIONS --

Returns:
  EAX = result (AL/AX for BYTE/WORD variants)

Registers:
 Clobbers:
  EAX EBX EDX ECX
 
 Preserves:
  ESI EDI EBP
 
Notes:
 ESP is restored before return
 [esp] contains the return address
 DIV/IDIV overwrite EDX (remainder is not preserved)

Flags:
  Modified according to operation

Calling convention:
  stdcall (callee cleans stack)

For 2 argument functions:
  [esp+4] = first argument
  [esp+8] = second argument

For 1 argument functions:
  [esp+4] = argument

+1003 is ADD DWORD. Takes 2 arguments in stack.
 Result in EAX

+1011 is ADD WORD. Takes 2 arguments in stack.
 Result in AX

+1022 is ADD BYTE.  Takes 2 arguments in stack.
 Result in AL

+1030 is AND DWORD.  Takes 2 arguments in stack.
 Result in EAX

+103E is AND WORD.  Takes 2 arguments in stack.
 Result in AX

+104F is AND BYTE.  Takes 2 arguments in stack.
 Result in AL

+105D is DIV DWORD.  Takes 2 arguments in stack.
 Result in EAX

+106D is DIV WORD.  Takes 2 arguments in stack.
 Result in AX

+1081 is DIV BYTE.  Takes 2 arguments in stack.
 Result in AL

+1091 is IDIV DWORD.  Takes 2 arguments in stack.
 Result in EAX

+10A0 is IDIV WORD.  Takes 2 arguments in stack.
 Result in AX

+10B3 is IDIV BYTE.  Takes 2 arguments in stack.
 Result in AL

+10C3 is IMUL DWORD. Takes 2 arguments in stack.
 Result in EAX

+10D1 is IMUL WORD. Takes 2 arguments in stack.
 Result in AX

+10E2 is IMUL BYTE. Takes 2 arguments in stack.
 Result in AL

+10F0 is MUL DWORD. Takes 2 arguments in stack.
 Result in EAX

+10FE is MUL WORD. Takes 2 arguments in stack.
 Result in AX

+110F is MUL BYTE. Takes 2 arguments  in stack.
 Result in AL

+111D is NOT DWORD. Takes 1 argument   in stack.
 Result in EAX

+1127 is NOT WORD. Takes 1 argument  in stack.
 Result in AX

+1133 is NOT BYTE. Takes 1 argument  in stack.
 Result in AL

+113D is OR DWORD. Takes 2 arguments  in stack.
 Result in EAX

+1150 is OR WORD. Takes 2 arguments  in stack.
 Result in AX

+115C is OR BYTE. Takes 2 arguments  in stack.
 Result in AL

+116A is XOR DWORD. Takes 2 arguments  in stack.
 Result in EAX

+1178 is XOR WORD. Takes 2 arguments  in stack.
 Result in AX

+1189 is XOR BYTE. Takes 2 arguments  in stack.
 Result in AL
```
