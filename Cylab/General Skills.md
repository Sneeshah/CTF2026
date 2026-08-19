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















