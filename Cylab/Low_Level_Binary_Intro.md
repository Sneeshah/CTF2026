# Low_Level_Binary_Intro

## Description:
Some introduction to binary hacking, assembly, python etc

### Obedient Cat
#### This file has a flag in plain sight (aka "in-the-clear").

  1) strings flag
  2) picoCTF{s4n1ty_v3r1f13d_9b8fa0bc}
  

### Warmed Up
#### What is 0x3D (base 16) in decimal (base 10)?

  1) picoCTF{61}


### ASCII Numbers
#### Convert the following string of ASCII numbers into a readable string

  1) picoCTF{45c11_n0_qu35710n5_1ll_t311_y3_n0_l135_445d4180}


### Picker I
#### This service can provide you with a random number, but can it do anything else?

  1) whole program works through a while(True) loop with an eval(user_input + '()') inside
  2) Flag is printed if win() is called so we can just input 'win' to call that function since eval() will interpret it as python code
  3) 0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x63 0x65 0x34 0x62 0x35 0x64 0x35 0x62 0x7d
  4) picoCTF{4_d14m0nd_1n_7h3_r0ugh_ce4b5d5b}


### Bit-O-Asm-1
#### Can you figure out what is in the eax register? Flag is hex into dec.
  1) mov    eax,0x30
  2) so 0x30 is in eax, 0x30 is 48 in dec
  3) picoCTF{48}


### Bit-O-Asm-2
#### Can you figure out what is in the eax register?

  1) mov    DWORD PTR [rbp-0x4],0x9fe1a
     mov    eax,DWORD PTR [rbp-0x4]
  2) so 0x9fe1a is in eax
  3) picoCTF{654874}


### Bit-O-Asm-3
#### Can you figure out what is in the eax register?

  1) DWORD PTR [rbp-0xc],0x9fe1a       // 0x9fe1a is moved to dword at rbp-0xc
     mov    DWORD PTR [rbp-0x8],0x4    // 0x4 is moved to dword at rbp-0x8
     mov    eax,DWORD PTR [rbp-0xc]    // 0x9fe1a is moved to eax
     imul   eax,DWORD PTR [rbp-0x8]    // eax (0x9fe1a) becomes eax multiplied with rpb-0x8 (0x4)
     add    eax,0x1f5                  // eax (27f868) becomes eax + 0x1f5
  2) Note: math operations always save their result in the left operand
  3) so the flag is picoCTF{2619997}



### Bit-O-Asm-4
####  Can you figure out what is in the eax register?

  1) <+15>  mov    DWORD PTR [rbp-0x4],0x9fe1a     // 0x9fe1a is moved to dword at rbp-0x4
     <+22>  cmp    DWORD PTR [rbp-0x4],0x2710      // compare 0x2710 to rbp-0x4 (0x9fe1a)
     <+29>  jle    0x55555555514e <main+37>        // since the left operand of compare is bigger than the right one less or equal jump condition is not true -> no jump 
     <+31>  sub    DWORD PTR [rbp-0x4],0x65        // 0x65 is subtracted from dword at rbp-0x4 (0x9fe1a) and written to dword at rbp-0x4 (9FDB5)
     <+35>  jmp    0x555555555152 <main+41>        // jmp is made to <main+41>
     <+37>  add    DWORD PTR [rbp-0x4],0x65        // skipped cause of jump
     <+41>  mov    eax,DWORD PTR [rbp-0x4]         // dword at rbp-0x4 (9FDB5) is written to eax
  2) picoCTF{654773}


### GDB baby step 1
#### Can you figure out what is in the eax register at the end of the main function? 

  1) <+15>:    mov    eax,0x86342
  2) picoCTF{549698}


### GDB baby step 2
#### Can you figure out what is in the eax register at the end of the main function? 

  1) seting breakpoint after eax is written to last. break *main+59
  2) run -> info registers eax 
  3) picocTF{307019}


### GDB baby step 3
#### Now for something a little different. 0x2262c96b is loaded into memory in the main function. Examine byte-wise the memory that the constant is loaded in by using the GDB command x/4xb addr. The flag is the four bytes as they are stored in memory.

  1) break *main+22
  2) run -> x/4xb $rbp-0x4 (x stands for examine. This gives back 4 bites (b) in hex (x) at adress rbp-0x4 (where the constant was written to)
  3) picoCTF{0x6bc96222}


### GDB baby step 4
#### main calls a function that multiplies eax by a constant

  1) break *main+38 // where the function is called
  2) run -> stepi // step into the function
  3) picoCTF{12905}


### ASCII FTW
#### This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program.

  1) break after the all the hex ascii values are saved
  2) run and the flag is written there (might be due to jeff extension)
  3) picoCTF{ASCII_IS_EASY_7BCD971D}


### Picker II
#### Can you figure out how this program works to get the flag?

  1) same eval but this time there is a filter function looking for 'win'
  2) since win() uses open('flag.txt', 'r').read() we can just input that
  3) nvm str objects are not callable so we wrap it inside a print command and we get the flag
  4) picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_0b5f1131}
  5) another way is to just input eval('w'+'i"+'n') since this eval will be inside the programs eval it will be treated as code and then just does eval(win()) again, flag will be in hex then


### Picker III
#### Can you figure out how this program works to get the flag?

  1) seems better but really isnt.
  2) press 3 to rewrite a variable in the table
  3) choose the first one (print_table) and replace with win
  4) press 1 to execute the first function in the table
  5) picoCTF{7h15_15_wh47_w3_g37_w17h_u53r5_1n_ch4rg3_a186f9ac}


### Picker IV
#### Can you figure out how this program works to get the flag?

  1) ahhh C-Code
  2) void (*foo)(void) = (void (*)())val; is interesting. foo now holds the adress of a function val that returns void. But val is a user input.
  3) Since we got the binary we can use gdb and use print win to print the variable win
  4) picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_14bc5444}


### buffer overflow 0
#### Let's start off simple, can you overflow the correct buffer?

  1) program uses strcpy() which does not check for size of destination
  2) so we can just look at the size of the destination buf2 which is 16 bytes and copy more than 16 bytes to it for a buffer overflow
  3) picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}


### Local Target
#### Smash the stack

  1) program prints num is 64 and Bye whatever string we put in
  2) 64 is hardcoded, bye is too. But win is triggered if num is 65 somehow
  3) gets(method) is used for input - gets is suepr dangerous (even has a warning in man gets)
  4) so if we make our input with the right size we can override the whole buffer and then change num to 65 



















  
