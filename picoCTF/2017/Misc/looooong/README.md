# Misc (Level 1): looooong
## Description: 
>I heard you have some "delusions of grandeur" about your typing speed. How fast can you go at shell2017.picoctf.com:22531?
## Solution:
First, go to the webshell using netcat. 
***
    $ nc shell2017.picoctf.com 22531
    To prove your skills, you must pass this test.
    Please give me the 'Z' character '657' times, followed by a single '9'.
    To make things interesting, you have 30 seconds.
    Input:
***
Seems like we need to generate some quick output, so I decided to use python to do the work for me. 
*** 
    $ python -c "print 'Z' * 657"
Then I simply pasted the output, typed the additional '9', and hit enter. Boom.
***
    You git it! You're super quick!
    Flag: with_some_recognition_and_training_delusions_become_glimpses_fbafb1011720def036b5aa32671f3710
Therefore, flag is: with_some_recognition_and_training_delusions_become_glimpses_fbafb1011720def036b5aa32671f3710
