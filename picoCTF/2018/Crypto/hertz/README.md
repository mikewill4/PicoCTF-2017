# hertz
## Description
>Here's another simple cipher for you where we made a bunch of substitutions. Can you decrypt it? Connect with nc 2018shell.picoctf.com 48487
## Solution
First, connect to the shell with netcat and pipe the output to a file.
***
    $ nc 2018shell.picoctf.com 48487 > hertz.txt
***
You will actually get different output each time you connect to the shell, but
that isn't important. Since this is a simple substitution cipher (according to
the challenge) I copied the output and pasted it into
[quipqiup](https://quipqiup.com/) and it was able to crack it for me. Flag:
picoCTF{substitution_ciphers_are_solvable_cdilgndlnp}
