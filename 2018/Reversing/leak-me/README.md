# leak-me
## Description
>Can you authenticate to this service and get the flag? Connect with nc 2018shell.picoctf.com 31045
## Solution
Analyzing the code you can see that there are buffers for the name and password.
Since both come from user input you can try to break the program by providing
input longer than the buffer size. It turns out that providing a long name leaks
the password: a_reAllY_s3cuRe_p4s$word_d98e8d

Then you can use the password to get the flag: picoCTF{aLw4y5_Ch3cK_tHe_bUfF3r_s1z3_d1667872}
