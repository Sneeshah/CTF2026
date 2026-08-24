
Found here: https://overthewire.org/wargames/bandit/

# Bandit


## Description:
The Bandit wargame is aimed at absolute beginners. It will teach the basics needed to be able to play other wargames.


### Level 0
#### Connect to the game.The password for the next level is stored in a file called readme located in the home directory

 1) ssh bandit0@bandit.labs.overthewire.org -p 2220
 2) ls The password for the next level is stored in a file called readme located in the home directory
 3) cat readme
 4) 6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR

### Level 1
#### The password for the next level is stored in a file called - located in the home directory

  1) interesting name for a file
  2) cat ./- or cat <- works to get the file content
  3) PK8fYLZg2hnHSz83plBL1iEPKdD3QToB

### Level 2
#### The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

  1) Same solution as last level
  2) 7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME

### Level 3
#### The password for the next level is stored in a hidden file in the inhere directory.

  1) cd inhere/
  2) ls -la (a shows hidden (. / ..) files and directories
  3) cat ./...Hiding-From-You
  4) xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq

### Level 4
#### The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

  1) cd inhere/
  2) ls -la
  3) well we can cat every single file or even type and cat every single one but there should be a better way
  4) quick google search -> find ./ -type f -name "*" -exec file "{}" \;
  5) so file 7 is readable
  6) cat ./-file-7
  7) 6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG

### Level 5
#### The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

  1) gonna do this next time, looks like we gotta use a specific configuration of the find command






















