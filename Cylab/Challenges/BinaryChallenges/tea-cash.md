# tea-cash

#### You’ve stumbled upon a mysterious cash register that doesn’t keep money — it keeps secrets in memory. Traverse the free list and find all the free chunks to get to the flag. 

 1) Looking at the makefile we can see how the vulnerable file was build.
 2) gcc -Xlinker -rpath=./ -Wall -m64 -pedantic -no-pie --std=gnu99 -o heapedit heapedit.c
 3) so it is a 64-bit binary (m64), PIE is not enabled and the c standard is c99
 4) The file is called heapedit.c so might need to overflow into heap again
 5) So that program creates 6 chunks each having 0x80 = 128 bytes. %p is used to show addresses to us and to validate we input a real address
 6) yeah problem here is I can not run gdb runs some errors and the fixes I found did not work. I looked at walkthroughs to see if there are any that went into gdb and fixed it but found none
 7) https://blog.quarkslab.com/heap-exploitation-glibc-internals-and-nifty-tricks.html this is what I use to understand this thing since I saw it comeup in a walkthrough so it surely will have all the knowledge I need
 8) putting my notes from that site into a seperate repo here [heap exploitation notes](https://github.com/Sneeshah/Notes/blob/main/heap_exploitation/heap_exploitation.md)
 9) decided to give it a try after working through one third of the above blog. Well this was easy - the only thing I was missing earlier is the fact that the chunks also have that 0x10 header and they always round up to the closest 0x10. In this case 0x90. 
 10) meaning when the program is run we just have to count +0x90 to every adress
 11) picoCTF{c684a9e71f2066200e5627ee544bd71a}
