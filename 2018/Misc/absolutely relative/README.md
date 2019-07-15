# absolutely relative
## Description
>In a filesystem, everything is relative ¯\_(ツ)_/¯. Can you find a way to get a
>flag from this
>[program](https://2018shell.picoctf.com/static/725b533a89a0e70b85b37ce2965da003/absolutely-relative)? You can find it in /problems/absolutely-relative_2_69862edfe341b57b6ed2c62c7107daee on the shell server.
## Solution
The program in this challenge is trying to read a file "./permission.txt", but
it doesn't have permission to read it. The way to get around this issue is to
create your own permission.txt file in a place that you have access rights to
such as your home directory ~. Then simply put the word "yes" in the file and
save it. Then execute the program from that directory by using the full path to
it
/problems/absolutely-relative_2_69862edfe341b57b6ed2c62c7107daee/absolutely-relative
and you get the flag.

Flag: picoCTF{3v3r1ng_1$_r3l3t1v3_372b3859}
