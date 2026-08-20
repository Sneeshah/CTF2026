# Sleuthkit Series


## Description:
No idea what it is about, but it is labeled a medium difficulty task.


### Sleuthkit Intro

#### Question: Download the disk image and use mmls on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.

  1) pretty straight forward, gzip to extract it in /tmp then mmls to find the size of the linux partition'
  2) mmls does the rest, the size is 202752 sectors.
  3) picoCTF{mm15_f7w!}
  4) Note: mmls displayes the layout of media and disk images and prints the partitions, that way I can find offsets to analyze later

### Sleuthkit Apprentice

#### Question: Download this disk image and find the flag.
Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory.

  1) This time we are not told to connect to a remote checker, so the question is how do we extract the flag. 
  2) there is Linux swap partition and two linuix partitions with different sizes on it
  3) kurze Google suche sagt, dass der erste Schritt fsstat seins sollte also
  4) fsstat -o [start] [partition] leider bei der ersten Partition nichts, aber bei der zweiten steht bei einzelnen Gruppen immer wieder flags
  5) mit fls -o sieht man zwar die einzelnen drectories aber da sticht jetzt auch nichts ins Auge
  6) using fls -r -o disk.flag.img | grep -i "flag" returns back two txt-files
  7) bit of googling around revealed the icat tool to output file conments based on the inode numbers (we got them last step)
  8) icat -o 360448 disk.flag.img 2371 > flag.txt does the trick
  9) picoCTF{by73_5urf3r_adac6cb4}
