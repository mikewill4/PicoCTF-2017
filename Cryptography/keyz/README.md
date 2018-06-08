# Cryptography (Level 1): keyz
## Description: 
>While webshells are nice, it'd be nice to be able to login directly. To do so, please add your own public key to ~/.ssh/authorized_keys, using the webshell. Make sure to copy it correctly! The key is in the ssh banner, displayed when you login remotely with ssh, to shell2017.picoctf.com
## Solution:
This is a pretty straightforward question. There is a LOT of webpages that will
tell you how to generate the public key for this challenge. Here is how I did
it:
***
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub > authorized_keys
ssh shell2017.picoctf.com
***
Flag: `who_needs_pwords_anyways` 
