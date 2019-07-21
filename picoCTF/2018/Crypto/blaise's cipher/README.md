# blaise's cipher
## Description
>My buddy Blaise told me he learned about this cool cipher invented by a guy also named Blaise! Can you figure out what it says? Connect with nc 2018shell.picoctf.com 18981
## Solution
As hinted at by the problem, this is a Vigenere cipher. Unfortunately we don't
have the key or even a key length though. Luckily after pasting the ciphertext
in a series of online decoders I found that [Vigenere
Solver](https://www.guballa.de/vigenere-solver) worked. The key turned out to be
"flag". Flag: picoCTF{v1gn3r3_c1ph3rs_ar3n7_bad_095baccc}
