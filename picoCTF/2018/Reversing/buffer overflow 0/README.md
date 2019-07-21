# buffer overflow 0
## Description
>Let's start off simple, can you overflow the right buffer in this program to get the flag?
## Solution
When you run the program, it prompts you to provide an argument. The source code
shows that the provided argument is passed to the vuln function and copied into
a 16 byte buffer before being printed. Simply provide input that is greater than
the buffer size to dump the flag.
***
    $ ./vuln aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
    picoCTF{ov3rfl0ws_ar3nt_that_bad_2d11f6cd}
***
