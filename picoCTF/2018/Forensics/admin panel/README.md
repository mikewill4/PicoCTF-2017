# admin panel
## Description
>We captured some [traffic](https://2018shell.picoctf.com/static/162c41cc965c3db31c3acffecc3b2c87/data.pcap) logging into the admin panel, can you find the password?
## Solution
The download is a pcap, so naturally I opened it up in Wireshark. Once you have
it open in Wireshark you will see a bunch of traffic. Since this is a logon
attempt, we can just look at the HTTP traffic. After looking through the parsed
text sections of the HTTP packets you will eventually find the flag:
picoCTF{n0ts3cur3_df598569}

