# Forensics in CTF's

## Description:
Follow along in the Challenge Library with these instructional videos on Forensics topics.


### information
#### Files can always be changed in a secret way. Can you find the flag?

  1) tried stegseek with rockyou password list but no valid passphrase. steghide said it needs one.
  2) damn I missed something in the metadata. The license field is nonsense. Looks like base64 (only numbers and letters)
  3) cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
  4) picoCTF{the_m3tadata_1s_modified}  


### Glory of the Garden
#### This file contains more than it seems.

  1) This time exif metadata looks normal
  2) strings command easily gets the flag at the end though
  3) picoCTF{more_than_m33ts_the_3y339140129}

### Enhance! and Sleuthkit into
#### Aleady solved in another Learning Path

### Disk, Disk, sleuth
#### Use srch_strings from the sleuthkit and some terminal-fu to find a flag in this disk image.

  1) srch_strings dds1-alpine.flag.img | grep pico
  2) picoCTF{f0r3ns1c4t0r_n30phyt3_5e56e786}
  3) srch_strings apparently is the same as strings

### Disk, disk, sleuth! II
#### All we know is the file with the flag is named down-at-the-bottom.txt...

  1)  mmls dds2-alpine.flag.img
  2)  fls -r -o 2048 dds2-alpine.flag.img | grep down-at-the-bottom.txt
  3)  icat -o 2048 dds2-alpine.flag.img 18291
  4)  picoctf{f0r3ns1c4t0r_n0v1c3_4bd721f2}
  5)  Note: For forensice mmls, fls and icat are mandatory. Icat takes -o <offset> img-file <file inode> to extract a file
  
### Extensions
#### This is a really weird text file. Can you find the flag?

  1) strings did nothing
  2) AH, file flag.txt showed it is a png
  3) picoCTF{now_you_know_about_extensions}

### St3g0
#### Download this image and find the flag.

  1) exiftool looks normal
  2) binwalk also does nothing but zsteg -a pico.flag.png instantly extracted the flag
  3) picoCTF{7h3r3_15_n0_5p00n_96ae0ac1}

### What Lies Within
#### There's something in the building. Can you retrieve the flag?

  1) zsteg instantly found it again
  2) picoCTF{h1d1ng_1n_th3_b1t5}

### Packets Primer
#### Download the packet capture file and use packet analysis software to find the flag.

  1) open the file in wireshark and go through the packets anb it is there in the fourth packet
  2) picoCTF{p4ck37_5h4rk_b9d53765}

### Wireshark doo dooo do doo...
#### Can you find the flag?

  1) not as easy aws the last one but I filtered for http and found a http packet that text/html as "Info"
  2) cvpbPGS{c33xno00_1_f33_h_qrnqorrs} this looks like a flag?
  3) picoCTF{p33kab00_1_s33_u_deadbeef} (after using rot13)

### Trivial Flag Transfer Protocol
#### Figure out how they moved the flag.

  1) I found the files since it is the TFTP protocol used to transer files
  2) There are 3 pictures and a rot13 encrypted text that seems useless, piuctures show different angels of a cliff
  3) Since the text had a weird wording: Due-Diligence this might be the passphrase and for picture 3 it actually worked
  4) picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
