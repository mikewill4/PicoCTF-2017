# Play Time
## Description
>Rick just loves to play some good old videogames. can you tell which game is he playing? whats the IP address of the server?
## Solution
Run a pslist with volatility to find running processes.
***
	$ ./vol.py -f OtterCTF.vmem --profile=Win7SP1x64 pslist
	...
	0xfffffa801b5cb740 LunarMS.exe             708   2728     18      346      1      1 2018-08-04 19:27:39 UTC+0000
	...
***
You'll see a LunarMS.exe. LunarMS appears to be the only game that was running. Now let's find the server IP. I'll use netscan again, but this time I will grep for LunarMS.
***
	$ ./vol.py -f OtterCTF.vmem --profile=Win7SP1x64 netscan | grep LunarMS
	Volatility Foundation Volatility Framework 2.6
    0x7d6124d0         TCPv4    192.168.202.131:49530          77.102.199.102:7575  CLOSED           708      LunarMS.exe
    0x7e413a40         TCPv4    -:0                            -:0                  CLOSED           708      LunarMS.exe
    0x7e521b50         TCPv4    -:0                            -:0                  CLOSED           708      LunarMS.exe
***
The first entry has the server IP.

Flags:
CTF{LunarMS}
CTF{77.102.199.102}
