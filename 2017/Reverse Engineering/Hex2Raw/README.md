# Reverse Engineering (Level 1): Hex2Raw
## Description: 
>This program requires some unprintable characters as input...But how do you print unprintable characters? CLI yourself to /problems/88518d23aee7ee21e50bdd8414a404c1 and turn that Hex2Raw!
## Solution:
The description tells us that we will need to produce some input for a program. So I started off by running the program to see if it would provide any indication as to what input it wanted. 
***
    $ cd /problems/88518d23aee7ee21e50bdd8414a404c1 
    $ ./hex2raw
    Give me this in raw form (0x41 -> 'A'):
    7ca67167db329a5d1508cc4ad5380678
***
Easy enough! All we need to do is convert that hex to ascii and pipe it into the hex2raw program as input.
***
    $ echo "7ca67167db329a5d1508cc4ad5380678" | xxd -r -p | ./hex2raw
    Give me this in raw form (0x41 -> 'A'):
    7ca67167db329a5d1508cc4ad5380678

    You gave me:
    7ca67167db329a5d1508cc4ad5380678
    Yay! That's what I wanted! Here be the flag:
    75d3080d00407fa709c18a6cc69d1edc
***
Therefore, flag is: `75d3080d00407fa709c18a6cc69d1edc`
