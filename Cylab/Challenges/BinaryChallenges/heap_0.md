# heap 0

#### Question: Are overflows just a stack concern?

 1) that programm uses scanf with the format specifier %s which is not secure since that way scanf just reads input data until it hits a whitespace.
     - interesting to note here is that scanf("%20s", input) actually writes 21 bytes (20 + \0 to terminate) so if input was declared like char buffer [20] it would overflow by 1
 2) 
