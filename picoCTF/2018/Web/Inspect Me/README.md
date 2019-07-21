# Inspect Me
## Description
>Inpect this code! http://2018shell.picoctf.com:56252
## Solution
The title of this challenge hints that we need to inspect the HTML elements of
the provided webpage. Find the developer tools option in your browser and start
picking through the HTML. Inside of the "tababout" div you will find:
***
    <!-- I learned HTML! Here's part 1/3 of the flag: picoCTF{ur_4_real_1nspe
    -->
***
Great! Now we just need to keep looking for the other parts of the flag. If you
navigate to the "Sources" tab you will find that there is a mycss.css file and
myjs.js file. When looking at the mycss.css file you will find:
***
    /* I learned CSS! Here's part 2/3 of the flag: ct0r_g4dget_9dd3b33c} */
***
Finally, looking at myjs.js you will find:
***
    /* I learned JavaScript! Here's part 3/3 of the flag: */
***
Put all of the pieces together and you're done.
