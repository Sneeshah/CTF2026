# Echo Escape 1

#### The "secure" echo service welcomes you politely… but what if you don’t stay polite? Can you make it reveal the hidden flag? 

 1) first I tried a couple of inputs but not much happening
 2) interesting line in code: read(0, buf, 128). This means that upto 128 bytes can be written to buf from stdin (0).
 3) The problem is buf is declared with 32 bytes of size so thats our overflow
 4) I used https://zerosum0x0.blogspot.com/2016/11/overflow-exploit-pattern-generator.html for offset again since gdb seems to be off with them
 5) After running gdb with 160 bytes of input we see that vuln stopped due to SIGSEGV and 0Ab1Ab2A is shown to be inside $rbp
 6) That is our overflow offset 0Ab1Ab2A => 32 bytes of overflow. Makes sense, as this just overrides the whole buffer.
 7) Now we need to override rbp (8 bytes) and then we can add the return adress we want to jump to win()
 8) Need to keep little endian in mind again
 9) With python: python -c 'print("A" * 40 + "\x56\x12\x40\x00\x00\x00\x00\x00")' | nc mysterious-sea.picoctf.net 54986
 10) picoCTF{3ch0_s3rv1c3_br34k5_c767e3aa}
 11) **_Note_** the better way to use read() is to use sizeof(buf) instead of manually coding or calculating the size of the buffer
 12) 
