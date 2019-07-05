# Aca-Shell-A
## Description
>It's never a bad idea to brush up on those linux skills or even learn some new ones before you set off on this adventure! Connect with nc 2018shell.picoctf.com 42334.
## Solution
Start by using netcat to get into the shell.
***
    $ nc 2018shell.picoctf.com 42334
***
Now I started poking around the filesystem to see what was there.
***
    $ ls
    blackmail
    executables
    passwords
    photos
    secret
***
After inspecting each directory, secret was the only one with files in it. Next
you have to delete all of the intel files.
***
    $ cd secret
    $ rm intel*
***
Then you are told that an exploit is dropped in the executables folder.
***
    $ echo 'Drop it in!'
    $ cd ,,
    $ cd executables
    $ ls
    dontLookHere
    $ ./dontLookHere
***
Next you are asked for the username of the system you are on. A big hint is
that you have to print it without echo.
***
    $ whoami
    l33th4x0r
***
Finally you have to copy the TopSecret documents over to the passwords folder
and read it.
***
    $ cp /tmp/TopSecret passwords/
    $ cd ..
    $ cd passwords
    $ cat TopSecret
    Major General John M. Schofield's graduation address to the graduating class of 1879 at West Point is as follows: The discipline which makes the soldiers of a free country reliable in battle is not to be gained by harsh or tyrannical treatment.On the contrary, such treatment is far more likely to destroy than to make an army.It is possible to impart instruction and give commands in such a manner and such a tone of voice as to inspire in the soldier no feeling butan intense desire to obey, while the opposite manner and tone of voice cannot fail to excite strong resentment and a desire to disobey.The one mode or other of dealing with subordinates springs from a corresponding spirit in the breast of the commander.He who feels the respect which is due to others, cannot fail to inspire in them respect for himself, while he who feels,and hence manifests disrespect towards others, especially his subordinates, cannot fail to inspire hatred against himself.
    picoCTF{CrUsHeD_It_d6f202f1}
***

