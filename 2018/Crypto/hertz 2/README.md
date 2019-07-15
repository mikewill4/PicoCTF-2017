# hertz 2
## Description
>This flag has been encrypted with some kind of cipher, can you decrypt it? Connect with nc 2018shell.picoctf.com 12521
## Solution
My initial thought was to plug this into [quipqiup](https://quipqiup.com/) which
gave me the following result:
***
    The ?uic? bro?n fo? ?um?s over the la?y do?. I can't believe this is such an easy ?roblem in ?ico. It's almost as if I solved a ?roblem already! O?ay, fine. Here's the fla?: ?icoCTF{substitution_ci?hers_are_too_easy_?mnibirtnv}
***
This was nearly the flag, but the flag had substituion cipher in it, so I
searched for a substitution cipher solver. I found that
[guballa](https://www.guballa.de/substitution-solver) had one that gave me the
flag: picoCTF{substitution_ciphers_are_too_easy_gmnibirtnv}

