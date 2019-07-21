# Crypto Warmup 1
## Description
>Crypto can often be done by hand, here's a message you got from a friend,
>llkjmlmpadkkc with the key of thisisalilkey. Can you use this [table](https://2018shell.picoctf.com/static/ac0f6ae1aadadc4736c8b8478145bf8d/table.txt) to solve it?
## Solution
Initially I thought I had to match each letter up from the ciphertext and the
key, using the letter columns from the table for the ciphertext and letter rows
from the table for the key. However, this approach gave me ESSBUDMAOUOA, which
is gibberish. I then thought about what type of cipher would be able to make use
of the table and the fact that there was a key made me think Vigenere.

Surely enough it turned out to be Vigenere. I'm lazy so instead of actually
using the table I went back over to
[decode.fr](https://www.dcode.fr/vigenere-cipher) and was able to get the flag:
secretmessage
