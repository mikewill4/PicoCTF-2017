# Forensics Warmup 1
## Description
> Can you unzip this [file](https://2018shell.picoctf.com/static/8483d8ac0beca391b8322bc414773cfc/flag.zip) for me and retrieve the flag?
## Solution
Usually whenever I have a challenge involving zip files I first try to extract
with binwalk.
***
    $ binwalk -e flag.zip
***
And just like that binwalk was able to extract a flag.png
![Flag]()
