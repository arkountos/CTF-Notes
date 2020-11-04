# CTF-Notes
A list of notes to be referenced while playing CTFs

## Web
- Port 445 open -> Think SMB. SMB tools:
    - Nmblookup
    - nbtscan
    - SMBMap
    - Smbclient
    - Rpcclient
    - Nmap
    - Enum4linux


## Reverse Engineering / Binary
- When given an ELF file, I can use Ghidra to decompile it (go from executable to C source code!)
https://security.stackexchange.com/questions/204876/what-is-the-difference-between-ghidra-and-ida (I find Ghidra more straightforward and it has the Decompiler, whereas IDA has a debugger)
- Introduction to ROP https://codearcana.com/posts/2013/05/28/introduction-to-return-oriented-programming-rop.html
- GDB Interface for better readability: https://github.com/cyrus-and/gdb-dashboard
- `readelf` command
- `dmesg` shows info about all the segfaults!
- use `cat` right after you pass the payload to a binary to capture the shell! For example: `( python -c "print 'A'*20 + '\xcc\xba\x13\xca'" ; cat ) | ./vulnerable_binary` (from https://www.youtube.com/watch?v=yH8kzOkA_vw&list=PL1H1sBF1VAKVg451vJ-rx0y_ZuQMHPamH @ 5:45)

## Forensics
