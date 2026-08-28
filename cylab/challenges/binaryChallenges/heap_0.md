# heap 0

#### Question: Are overflows just a stack concern?

 1) damn heap overflows are again different and complicated ...
 2) so I know malloc makes the variable use space in heap not stack
 3) malloc() is used on input_data and safe_var. input_data is "pico" and safe_var = bico
 4) check(win) will check if safe_var is bico and if so we do not get the flag. SO we need to change safe_var by overflowing
 5) input_data is first filled with scanf("%s", input_data) which is dangerous since the buffer size is missing so we can overflow input_data
 6) in gdb I set a break point at *init+62 (malloc for input data)
 7) then I took a look at the accessible adress space (info proc mappings) - this was useless after all
 8) I used p safe_var and p input_data to print the adresses of both variables. Their differnece is 0x20 = 32 bytes.
 9) I was confused for a while by math until I found out that malloc automatically reserves 32 bytes here. This means byte 0 is the beginning of input_data and byte 32 is the beginning of safe_var
 10) SO I can input 32 letters and then a p to change "bico" to "pico" and get the flag
 11) picoCTF{my_first_heap_overflow_0c473fe8}
