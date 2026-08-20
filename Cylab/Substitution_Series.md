# Substitution Series


## Description:
No idea what it is about, but it is labeled a medium difficulty task.


### substitution0

#### Question: A message has come in but it seems to be all scrambled. Luckily it seems to have the key at the beginning. Can you crack this substitution cipher?

 1) cat message.txt shows a message with smth that looks like a flag just with a ceaser cipher so I will try cyberchef
 2) okay so it is not simply rotated, let's try frequency analysis. https://www.dcode.fr/frequency-analysis is what I used years ago and it seems to still work
 3) Don't forget to tick the right box so it suggests a transcription and keeps the word borders
 5) picoCTF{5UB5717U710N_3V0LU710N_357BF9FF} 

### substitution1

#### A second message has come in the mail, and it seems almost identical to the first one. Maybe the same thing will work again.

 1) got a feeling it wont work again but we can try
 2) picoCTF{FR3JU3NCY_4774CK5_4R3_C001_6E0659FB} this is what I get but it does not work for some reason.
 3) using quipquip I found it the J in the above flag needs to be a q. Note: look twice at those super low frequency letters if something doesn't add up
 4) picoCTF{FR3QU3NCY_4774CK5_4R3_C001_6E0659FB}

### substitution2

#### It seems that another encrypted message has been intercepted. The encryptor seems to have learned their lesson though and now there isn't any punctuation! Can you still crack the cipher?

1) same thing again, we don't care for spaces with out tools though
2) PICOCTF{N6R4M_4N41Y515_15_73D10U5_8E1BF808} 
