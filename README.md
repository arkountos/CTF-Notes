# CTF-Notes
A list of notes to be referenced while playing CTFs

## Web
- Search exploits on the net (exploit-db or google) and *not* on metasploit. Not every module you need is already shipped with metasploit!
- Port 3306 (mysql): https://book.hacktricks.xyz/pentesting/pentesting-mysql 
- `wp-login.php` and `wp-admin.php` for wordpress
- When enumerating directories, also try names with .tar, .zip, .js, .php, .html extensions!
- Port 445 open -> Think SMB. SMB tools:
    - Nmblookup
    - nbtscan
    - SMBMap
    - Smbclient
    - Rpcclient
    - Nmap
    - Enum4linux
    
Also `eternalblue` came out in 2017 and it utilizes SMB vulnerabilities


## Reverse Engineering / Binary
- When given an ELF executable, I can use Ghidra, Cutter to decompile it (go from executable to C source code)
- LD_PRELOAD tricks. You can specify your own standard library functions, like `malloc` or `strcmp`, in a custom library, then use LD_PRELOAD to load this library before the standard C one. Now when the program uses `malloc` your custom code will run instead of the standard malloc code. A crackme solution that overrides the `strcmp` function to solve it: https://crackmes.one/static/solution/5f09c44a33c5d42a7c667979.zip (ZED-Crackme)

### Assembly / C
- Assembly syntax difference example between Intel and AT&T:
    - Intel `movl $5, %eax`
    - AT&T `mov eax, 5`
- `malloc()` allocates a block of memory *in the heap* and returns the address (e.g. in the eax register)
- GDB Interface for better readability: https://github.com/cyrus-and/gdb-dashboard

### Binary / ROP
- Introduction to ROP https://codearcana.com/posts/2013/05/28/introduction-to-return-oriented-programming-rop.html
- `readelf` command
- `dmesg` shows info about all the segfaults!
- use `cat` right after you pass the payload to a binary to capture the shell! For example: `( python -c "print 'A'*20 + '\xcc\xba\x13\xca'" ; cat ) | ./vulnerable_binary` (from https://www.youtube.com/watch?v=yH8kzOkA_vw&list=PL1H1sBF1VAKVg451vJ-rx0y_ZuQMHPamH @ 5:45)

## Forensics
