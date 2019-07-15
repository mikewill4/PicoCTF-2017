# caesar cipher 2
## Description
>Can you help us decrypt this
>[message](https://2018shell.picoctf.com/static/732681495a458d226b12ae9f5e1b2730/ciphertext)? We believe it is a form of a caesar cipher. You can find the ciphertext in /problems/caesar-cipher-2_3_4a1aa2a4d0f79a1f8e9a29319250740a on the shell server.
## Solution
The challenge flat out tells you it is a caesar cipher. The challenge here is to
determine the alphabet. There are numbers, lowercase letters, uppercase letters,
and special characters. Because of the special characters, I decided to search
for an [ASCII table](http://www.asciitable.com/) to help me come up with a
reasonable alphabet. After trial and error, I was able to find that a ROT34 with
the alphabet "
!"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_`abcdefghijklmnopqrstuvwxyz{|}"
produced the flag.

Flag: picoCTF{cAesaR_CiPhErS_juST_aREnT_sEcUrE}
