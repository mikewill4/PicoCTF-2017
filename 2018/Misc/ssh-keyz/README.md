# ssh-keyz
# Description
As nice as it is to use our webshell, sometimes its helpful to connect directly to our machine. To do so, please add your own public key to ~/.ssh/authorized_keys, using the webshell. The flag is in the ssh banner which will be displayed when you login remotely with ssh to with your username.
# Solution
Simply generate your ssh key.
***
    $ ssh-keygen
***
Then add it to the authorized hosts file.
***
    $ cat ~/.ssh/id_rsa.pub > ~/.ssh/authorized_keys
***
Finally, ssh into the webshell to get the flag.
***
    $ ssh <your_username>@2018shell4.picoctf.com
    The authenticity of host '2018shell4.picoctf.com (18.188.70.152)' can't be established.
    ECDSA key fingerprint is SHA256:1/2OUR2IggrhZwLysFuJlUZ169yf1BFVeTIDW8Fo5XU.
    Are you sure you want to continue connecting (yes/no)? yes
    Warning: Permanently added '2018shell4.picoctf.com,18.188.70.152' (ECDSA) to the list of known hosts.
    picoCTF{who_n33ds_p4ssw0rds_38dj21}
***
Done.

