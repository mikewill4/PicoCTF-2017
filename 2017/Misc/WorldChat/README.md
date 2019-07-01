# Misc (Level 1): WorldChat
## Description: 
>We think someone is trying to transmit a flag over WorldChat. Unfortunately, there are so many other people talking that we can't really keep track of what is going on! Go see if you can find the messenger at shell2017.picoctf.com:61161.
## Solution:
We are given a domain and port, so we can pretty easily open up a webshell with netcat.
***
    $ nc shell2017.picoctf.com 61161
    worldchat v2.3002.4
    setting up readonly client...done
    connecting to feed...done
    Welcome to WORLDCHAT!
***
This produced far too much output so instead I grepped for 'flag'.
***
    $ nc shell2017.picoctf.com 61161 | grep flag
***
From that I was able to quickly spot the message `15:06:39 flagperson: this is part 1/8 of the flag - 1a2e`. From here, I could have searched for the rest of the parts manually, but I'm lazy so I altered my grep.
***
    $ nc shell2017.picoctf.com 61161 | grep flagperson
    15:11:17 flagperson: this is part 1/8 of the flag - 1a2e
    15:11:19 flagperson: this is part 2/8 of the flag - 3d0a
    15:11:19 flagperson: this is part 3/8 of the flag - 6310
    15:11:25 flagperson: this is part 4/8 of the flag - 682c
    15:11:29 flagperson: this is part 5/8 of the flag - 6be0
    15:11:29 flagperson: this is part 6/8 of the flag - e319
    15:11:37 flagperson: this is part 7/8 of the flag - d1b5
    15:11:46 flagperson: this is part 8/8 of the flag - 2f53
Put it all together: `1a2e3d0a6310682c6be0e319d1b52f53` 
