# assembly-1
## Description
>What does asm1(0xc8) return? Submit the flag as a hexadecimal value (starting with '0x').
## Solution
Through all the convoluted calls. It can be seen that the argument passed in is
never updated. At the very end of asm1 it is moved into eax and then 0x3 is
added to it. Therefore, the flag is 0xc8 + 0x3 = 0xcb.
