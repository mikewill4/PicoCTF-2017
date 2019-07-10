# Recovering From the Snap
## Description
>There used to be a bunch of [animals](https://2018shell.picoctf.com/static/5d982298cdb725f9e23c6f25c8a37411/animals.dd) here, what did Dr. Xernon do to them?
## Solution
There are many forensics tools out there for file carving. I used foremost for
this challenge. You can install foremost on mac with brew:
***
    $ brew install foremost
***
Then supply the animals.dd file as the input and an output directory for the
output.
***
    $ foremost -i animals.dd -o foremost_output
    Processing: animals.dd
    |*|
***
Then foremost will try to extract the files to foremost_output. I was able to
find that foremost extracted a bunch of jpg's and one of them contained the
flag: picoCTF{th3_5n4p_happ3n3d}
