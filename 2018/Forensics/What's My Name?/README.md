# What's My Name?
## Description
>Say my name, say [my
name](https://2018shell.picoctf.com/static/6ae91abb9e70e527e32729413103af90/myname.pcap)
## Solution
The question hints at DNS, which is used to resolve names of domains. If you
open up the pcap in Wireshark you can filter to just DNS packets and you will
find the flag: picoCTF{w4lt3r_wh1t3_033ad0f914a0b9d213bcc3ce5566038b}
