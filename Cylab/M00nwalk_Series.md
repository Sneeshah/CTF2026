# M00nwalk Series


## Description:
Test your forensics skills in this intermediate series.

### m00nwalk

#### Question: Decode this message from the moon.

 1) file is a .file so audio decryption probably, listening does not give me anything
 2) first couple of decoders, looking at hexdump etc brought nothing.
 3) First hint: How did pictures from the moon landing get sent back to Earth?
 4) A quick google search said the used unified s-band
 5) I found this decoded https://sstv-decoder.mathieurenaud.fr/ and it actually converted the file to a picture with the flag on it
 6) picoCTF{beep_boop_im_in_space}

### m00nwalk2

#### Revisit the last transmission. We think this transmission contains a hidden message. 

  1) same file as before so what are we looking for?
  2) used https://www.aperisolve.com/ to check for colour filters, alpha etc but can't quite see anything.
  3) According to the hint the clue files are needed it seems.
  4) using https://sstv-decoder.mathieurenaud.fr/ on all three clues
  5) first clue shows a picture: Password hidden_stegosaurus
  6) second clue: The quieter you are the more you can HEAR
  7) third clue: Alan Eliasen the FutureBoy
  8) https://www.boxentriq.com/steganography/steghide-extractor finally was a hit, puttin in the passphrase mentioned earlier gave us the flag
  9) picoCTF{the_answer_lies_hidden_in_plain_sight}
  10) could also use steghide in bash for that
  11) steghide --extract -sf message.wave -p hidden_stegosaurus
