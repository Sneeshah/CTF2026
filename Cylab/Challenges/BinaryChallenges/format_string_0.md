# format string 0

### Can you use your knowledge of format strings to make the customers happy?

  1) No idea how format strings attack work, found this one here: https://owasp.org/www-community/attacks/Format_string_attack
  2) https://www.exploit-db.com/docs/english/28476-linux-format-string-exploitation.pdf is also a good resource
  3) Key here is the specifier %114 which makes printf expect a number with a width of 114 chars - there is none so it will print garba data to inflate the count
  4) This satisfies the condition if (count > 2 * BUFSIZE)
  5) After that “Cla%sic_Che%s%steak” has several %s specifiers that create undefined behaviour. %steak is not a specifier but printf still tries to process it - the program crashes
  6) picoCTF{7h3_cu570m3r_15_n3v3r_SEGFAULT_c8362f05}

