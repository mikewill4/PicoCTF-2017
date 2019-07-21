# strings
## Description
>Can you find the flag in this [file](https://2018shell.picoctf.com/static/e78981e684a62559baaef12a27f0e918/strings) without actually running it? You can also find the file in /problems/strings_0_bf57524acf558aca2081eb97ece8e2ee on the shell server.
## Solution
As indicated by the title of the challenge, you need to use the strings command.
So run strings on the file and grep for the flag.
***
    $ strings strings | grep pico
    picoCTF{sTrIngS_sAVeS_Time_c09b1444}
***
