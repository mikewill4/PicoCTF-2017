# environ
## Description
>Sometimes you have to configure environment variables before executing a program. Can you find the flag we've hidden in an environment variable on the shell server?
## Solution
Login to the shell server on the pico ctf website with your username and
password. Then use the printenv command to show the set environment variables.
***
    $ printenv
    SECRET_FLAG=picoCTF{eNv1r0nM3nT_v4r14Bl3_fL4g_3758492}
***
There are a bunch, but the very first one is the flag!
