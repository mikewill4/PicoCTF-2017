# pipe
## Description
>During your adventure, you will likely encounter a situation where you need to process data that you receive over the network rather than through a file. Can you find a way to save the output from this program and search for the flag? Connect with 2018shell.picoctf.com 2015.
## Solution
This involves using the pipe ("|") to redirect output on the command line. First
connect with nc and pipe the output to a file.
***
    $ nc 2018shell.picoctf.com 2015 > flag.txt
***
Next grep for the flag!
***
    $ grep pico flag.txt
    picoCTF{almost_like_mario_8861411c}
***
