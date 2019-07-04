# HEEEEEERE'S Johnny
## Description
>Okay, so we found some important looking files on a linux computer. Maybe they
>can be used to get a password to the process. Connect with nc
>2018shell.picoctf.com 5221. Files can be found here: [passwd](https://2018shell.picoctf.com/static/f36d468a19d53f9fe375b4e8f4bb84a4/passwd)
>[shadow](https://2018shell.picoctf.com/static/f36d468a19d53f9fe375b4e8f4bb84a4/shadow).
## Solution
So initally I tried to netcat into the address provided and was prompted for a
username and password.
***
    $ nc 2018shell.picoctf.com 5221
    Username: hello
    Password: world
    Failed Login!
***
Looks like we need to extract a username and password from the passwd and
shadown files. Let's take a look at them:
***
    $ cat passwd
    root:x:0:0:root:/root:/bin/bash
    $ cat shadow
    root:$6$IGI9prWh$ZHToiAnzeD1Swp.zQzJ/Gv.iViy39EmjVsg3nsZlfejvrAjhmp5jY.1N6aRbjFJVQX8hHmTh7Oly3NzogaH8c1:17770:0:99999:7:::
***
At a first glance the username is obviously root, so that is figured out. We
also can see that there is some sort of hashed password. The title of the
challenge has "Johnny" in it, which hints at a password cracking tool called
JohnTheRipper. I downloaded john the ripper from
https://github.com/magnumripper/JohnTheRipper.
***
    $ git clone https://github.com/magnumripper/JohnTheRipper
    $ cd JohnTheRipper
***
Then I copied the passwd and shadow files into the JohnTheRipper directory. Now
we can crack the password.
***
    $ cd ../run
    $ ./john passwd shadow
    Warning: detected hash type "sha512crypt", but the string is also recognized as "HMAC-SHA256"
    Use the "--format=HMAC-SHA256" option to force loading these as that type instead
    Warning: detected hash type "sha512crypt", but the string is also recognized as "sha512crypt-opencl"
    Use the "--format=sha512crypt-opencl" option to force loading these as that type instead
    Using default input encoding: UTF-8
    Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 256/256 AVX2 4x])
    Cost 1 (iteration count) is 5000 for all loaded hashes
    Proceeding with single, rules:Single
    Press 'q' or Ctrl-C to abort, almost any other key for status
    Almost done: Processing the remaining buffered candidate passwords, if any.
    Proceeding with wordlist:./password.lst, rules:Wordlist
    password1        (root)
    1g 0:00:00:02 DONE 2/3 (2019-07-04 17:47) 0.4385g/s 1350p/s 1350c/s 1350C/s 123456..john
    Use the "--show" option to display all of the cracked passwords reliably
    Session completed
***
As you can see, JohnTheRipper cracked the password! It is password1. Let's try
it out.
***
    $ nc 2018shell.picoctf.com 5221
    Username: root
    Password: password1
    picoCTF{J0hn_1$_R1pp3d_289677b5}
***
And there's the flag!
