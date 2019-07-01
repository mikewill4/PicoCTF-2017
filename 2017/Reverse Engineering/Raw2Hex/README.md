# Reverse Engineering (Level 1): Raw2Hex
## Description: 
>This program just prints a flag in raw form. All we need to do is convert the output to hex and we have it! CLI yourself to /problems/40b1e663252261e8203962486523629e and turn that Raw2Hex!
## Solution:
This one is very straight forward. Linux command line does the work for us!
***
    $ cd /problems/40b1e663252261e8203962486523629e 
    $ ./raw2hex | od -A n -t x1
    54 68 65 20 66 6c 61 67 20 69 73 3a 71 c2 8d b7 75 78 a8 0e 38 aa e0 d6 26 d8 53 a5
***
After cleaning up the output, flag is: `54686520666c61672069733a71c28db77578a80e38aae0d626d853a5`
