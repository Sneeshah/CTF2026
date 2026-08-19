# General Skills in CTF's


## Description:
Just som general skills in CTFs, unfortunately seems like it is mostly done as a video course with challenges attached.



### Lets Warum up

#### Question: If I told you a word started with 0x70 in hexadecimal, what would it start with in ASCII?

 1) cyberchef -> p
 2) Note: seems like they use picoctf 2019 for it so perfect warmup ig.

### 2warm

#### Question: Can you convert the number 42 (base 10) to binary (base 2)?

 1) 101010

### Warmed Up

####Quesion: What is 0x3D (base 16) in decimal (base 10)?

  1) 61

### Obedient Cat 

  1)picoCTF{s4n1ty_v3r1f13d_9b8fa0bc}
  2) just opend with notepad++

#### Question: This file has a flag in plain sight (aka "in-the-clear").

 1) cyberchef -> p
 2) Note: seems like they use picoctf 2019 for it so perfect warmup ig.

### Wave a flag

#### Question: Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...

  1) seems hex doecoded or smth, trying to run in linux
  2) file tells me to use help flag (-h)
  3) ./warm -h  | grep -o 'picoCTF{[^}]*}' | xclip -sel clip 
  4) picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}

### convertme.py

#### Run the Python script and convert the given number from decimal to binary to get the flag.

  1) Run the script, had to convert decimal to binary
  2) picoCTF{4ll_y0ur_b4535_762f748e}

### what's a net cat?

#### Using netcat (nc) is going to be pretty important. Can you connect to fickle-tempest.picoctf.net at port 49239 to get the flag?

  1) nc fickle-tempest.picoctf.net 52454 | grep -o 'picoCTF{[^}]*}' | xclip -selection clipboard 
  2) picoCTF{nEtCat_Mast3ry_95035DAa}

### Nice netcat...

#### There is a nice program that you can talk to by using this command in a shell: $ nc wily-courier.picoctf.net 64621, but it doesn't speak English...

  1) nc gives us lots of numbers. Used Cyberchef to transform them into ASCII
  2) picoCTF{g00d_k1tty!_n1c3_k1tty!_a94e7}

### Tab, Tab, Attack

#### Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames.

  1) picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}

### Python Wrangling

#### Python scripts are invoked kind of like programs in the Terminal...

  1) cat password.txt | python3 ende.py -d flag.txt.en
  2) picoCTF{4p0110_1n_7h3_h0us3_9c5f9bcf}

### Magikarp Ground Mission

#### Do you know how to move between directories and read files in the shell? Start the container, ssh to it, and then ls once connected to begin. Login via ssh as ctf-player with the password, 8c606eb1 on the host wily-courier.picoctf.net and port 56311.
  
  1) ssh ctf-player@wily-courier.picoctf.net -p 56311
  2) used a bunch of cat >> to append the parts of the flag together, maybe not the most beautiful since I had to manually delete the newlines to get the flag
  3) picoCTF{xxsh_0ut_0f_//4t3r_0b24fc4f}

### First Grep

#### Can you find the flag in the file? This would be really tedious to look through manually, something tells me there is a better way.

  1) grep -o 'picoCTF{[^}]*}' file | xclip -selection clipboarD
  3) picoCTF{grep_is_good_to_find_things_01aE5e9d}

#### First Find

#### Unzip this archive and find the file named 'uber-secret.txt'

  1) find -name uber-secret.txt
  2) picoCTF{f1nd_15_f457_ab443fd1}

### BigZip

#### Unzip this archive and find the flag

  1) grep -r -o 'picoCTF{[^}]*}'
  2) picoCTF{gr3p_15_m4g1c_ef8790dc}  

### Static ain't always noise

#### Can you look at the data in this binary? The bash script might help!

  1) run the script
  2) cat static.ltdis.strings.txt |  picoGrep.sh
  3) (picoGrep is the above chained grep into xclip command)
  4) picoCTF{d15a5m_t34s3r_20335e41}

### Strings it

#### Can you find the flag in file without running it?

  1) grep doesn't work here cause it is a binary file so we gotta use strings to extract the flag from the file called 'strings'
  2) strings strings | picoGrep.sh
  3) picoCTF{5tRIng5_1T_FB7D7Bb6}

### Plumbing

#### Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag?

  1) sounds like we use cat to write to a file
  2) nc fickle-tempest.picoctf.net 58282 | picoGrep.sh
  3) picoCTF{digital_plumb3r_8c8f3412}

### Super SSH

#### Using a Secure Shell (SSH) is going to be pretty important.
Can you ssh as ctf-player to titan.picoctf.net at port 55547 to get the flag?
You'll also need the password 1db87a14. If asked, accept the fingerprint with yes.

  1) took a moment since I forgot about the -p flag
  2) ssh ctf-player@titan.picoctf.net -p 55547
  3) picoCTF{s3cur3_c0nn3ct10n_45a48857}

### Mod 26

#### Cryptography can be easy, do you know what ROT13 is?

  1) ROT13 -> rotate 13 spots in the alphabet
  2) Cyberchef -> picoCTF{next_time_I'll_try_2_rounds_of_rot13_45559abd}
  3) gl with doing 2 rounds of rot13

### Bases

#### What does this bDNhcm5fdGgzX3IwcDM1 mean? I think it has something to do with bases.

  1) sounds like base64 challenge
  2) l3arn_th3_r0p35 (it was indeed base64)

### Insp3ct0r

#### Kishor Balan tipped us off that the following code may need inspection:

  1) obviously our goal is to inspect that webiste for the flags
  2) picoCTF{tru3_d3 is the first part. There is a comment about html so let's look at css 
  3) t3ct1ve_0r_ju5t is the second part. Third part could be in the javascript
  4) _lucky?302945a7} bingo

### Where are the robots

#### Can you find the robots?

  1) guess we gotta look at the robots.txt file of that website
  2) robots txt file tell us to look at /cc6b1.html so we just replace robots.txt with that
  3) picoCTF{ca1cu1at1ng_Mach1n3s_cc6b1}

### PW Crack 1

#### Can you crack the password to get the flag?

  1) just looked inside the python script to find the password to use it and get the flag
  2) picoCTF{545h_r1ng1ng_56891419}

#### PW Crack 2

#### Can you crack the password to get the flag?

  1) same thing as the last, but password is not in plain but in hex.
  2) 0x34 0x65 0x63 0x39
  3) picoCTF{tr45h_51ng1ng_9701e681}

#### PW Crack 3

  1) code shows they use md5 has so can easily reverse it.
  2) could also just iterate through the couple of password in the list by hand or code
  3) bvi level3.hash.bin is a way to view the hash file (bvi = binary editor)
  4) 1B 18 E1 31 6F 92 18 CC 5B 05 3E 1C EA 28 E0 2E (this should be the md5 hash)
  5) iteration through the list: picoCTF{m45h_fl1ng1ng_2b072a90}

#### Can you crack the password to get the flag?

#### PW Crack 4

  1) same problem, just 100 plain passwords instead of 7.
  2) copy and paste the list before a new loop to iterate through them instead of input
  3) picoCTF{fl45h_5pr1ng1ng_d770d48c}


#### Can you crack the password to get the flag?

#### PW Crack 5

#### Can you crack the password to get the flag?

  1) seems like we just gotta loop througgh the dictionary
  2) using while IFS loop to go through every line of the dictionary and piping it to my picoGrep.sh - but since the dictionary is quite big doing it in python directly should be faster (python opens only once not 10k times)
  3) jup in python it is instant: picoCTF{h45h_sl1ng1ng_40f26f81}

### Enhance

#### Download this image file and find the flag.

  1) opened in text editior and saw single letters and numbers
  2) picoCTF{3nh4nc3d_24374675}

### vault-door-training

#### Your mission is to enter Dr. Evil's laboratory and retrieve the blueprints for his Doomsday Project. The laboratory is protected by a series of locked vault doors. Each door is controlled by a computer and requires a password to open. Unfortunately, our undercover agents have not been able to obtain the secret passwords for the vault doors, but one of our junior agents obtained the source code for each vault's computer! You will need to read the source code for each level to figure out what the password is for that vault door. As a warmup, we have created a replica vault in our training facility.

  1) password is in the code
  2) picoCTF{w4rm1ng_Up_w1tH_jAv4_000AXPNPN0i}

### keygenme-py

  1) running the program I guess we gotta find the license key. Let's see if we can rewrite the python code
  2) globals at the top have a dynamic key part
  3) picoCTF{1n_7h3_kk3y_of_XXXXXXXX} but we gotta find the X's.
  4) Code checks for dynamic part and we can just copy that and print/append to our flag 08c46aa4
  5) picoCTF{1n_7h3_kk3y_of_08c46aa4}

### buffer overflow 0

#### Let's start off simple, can you overflow the correct buffer?

  1) most annoying one, did it locally instead of with netcat and ofc no matter what I do it did not work with my inputs (maybe canary problem)
  2) strcpy jsut copies from source to destination but does not check if the size of the destination is enough (16 bytes here) -> overflow
  3) picoCTF{ov3rfl0ws_ar3nt_that_bad_ef01832d}


