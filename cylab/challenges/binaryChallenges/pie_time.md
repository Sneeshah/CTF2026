# Pie Time

#### Question: Can you try to get the flag? Beware we have PIE!

 1) I looked at the code and thought I can just take the adress of win() from gdb and put it in for a quick solve
 2) ingored the comment or challenge name completely (did not know about PIE)
 3) PIE stands for Position-Indipendent Executable. it makes the OS pick a random adress to load the binary at. So jumps don't have absolute adresses but relative references.
 4) That means the main function and the win function are still at the same adresses relative to each other - like a fixed distance
 5) In this case the difference between main and win is 96 (in hex)
 6) So we can start the program and it will tell us the adress of main: 0x58a0421af33d
 7) we simply do the math and get our flag
 8) picoCTF{b4s1c_p051t10n_1nd3p3nd3nc3_f8845f06}

