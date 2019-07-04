# grep 2
## Description
>This one is a little bit harder. Can you find the flag in /problems/grep-2_0_783d3e2c8ea2ebd3799ca6a5d28fc742/files on the shell server? Remember, grep is your friend.
## Solution
First login to the interactive shell in the shell tab with your username and
password. Then cd to the provided problem directory.
***
    $ cd /problems/grep-2_0_783d3e2c8ea2ebd3799ca6a5d28fc742/files
***
Now we have a bunch of files to grep through, so we need to grep recursively
with the -r option.
***
    $ grep -r pico
    files5/file23:picoCTF{grep_r_and_you_will_find_24c911ab}
***
Easy enough.
