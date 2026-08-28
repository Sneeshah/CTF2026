# Quizsploit

#### Solve the quiz.
 1) is this a 32-bit or 64 bit ELF -> file vuln -> 64-bit
 2) What's the linking of the binary? -> file vuln -> dynamic
 3) Is the binary stripped or not stripped -> file vuln -> not stripped
 4) What is the size of the buffer in bytes? -> 0x15
 5) How many bytes are read into the buffer? -> 0x90
 6) Is there a buffer overflow vulnerability? -> yes
 7) Name a standard C function that could cause a buffer overflow in the provided C code. -> fgets
    - interesting thing to note is how fgets works though. Generally fgets is safer than gets.
    - The first argument is the start of a buffer/array. The second is the maximum number of characters to store and the third is for the input.
    - So if the maximum size is bigger than the size of the buffer/array there are overflows possible
 8) What is the name of the function which is not callend anywhere in the programm? -> win()
 9) What type of attack could exploit this vulnerability? -> buffer overflow
 10) How many bytes of overflow are possible? -> 0x90 - 0x15 = 0x7b
 11) What protection is enabled in thisbinary? -> checksec --file=vuln -> NX
     - Another interesting thing to note is NX. NX stands for No-eXecute. A flag that marks the stack and heal as data only - not executable.
     - So NX stops shellcode injection. Shellcode injection basically means to overwrite the buffer with your own code then redirect the return adress to said code instead of other parts of the program.
 12) What exploitation technique could bypass NX? -> ROP
     - ROP stands for Return-Oriented Programmings which basically is a method to chain together parts of the code that are already there to do what an attacker wants
     - The crazy thing is that libraries work too, libs is good target since it includes stuff like system()
 14) What is the adress of win()? gdb vuln -> info functions -> 401176
 15) Flag: picoCTF{my_bIn@4y_3xpl0it_fL@g_58c7b379}

  
