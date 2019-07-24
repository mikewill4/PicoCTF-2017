# What the password?
## Description
>you got a sample of rick's PC's memory. can you get his user password? format: CTF{...}
## Solution
The challenge provides a virtual memory image, which can easily be analyzed with [volatility](https://github.com/volatilityfoundation/volatility).

I first ran imageinfo on the image to get the profile.
***
	$ ./vol.py -f OtterCTF.vmem imageinfo
	Volatility Foundation Volatility Framework 2.6
	INFO    : volatility.debug    : Determining profile based on KDBG search...
          Suggested Profile(s) : Win7SP1x64, Win7SP0x64, Win2008R2SP0x64, Win2008R2SP1x64_23418, Win2008R2SP1x64, Win7SP1x64_23418
                     AS Layer1 : WindowsAMD64PagedMemory (Kernel AS)
                     AS Layer2 : FileAddressSpace (/home/mike/ctf-write-ups/OtterCTF/Memory Forensics/OtterCTF.vmem)
                      PAE type : No PAE
                           DTB : 0x187000L
                          KDBG : 0xf80002c430a0L
          Number of Processors : 2
     Image Type (Service Pack) : 1
                KPCR for CPU 0 : 0xfffff80002c44d00L
                KPCR for CPU 1 : 0xfffff880009ef000L
             KUSER_SHARED_DATA : 0xfffff78000000000L
           Image date and time : 2018-08-04 19:34:22 UTC+0000
     Image local date and time : 2018-08-04 22:34:22 +0300
***
After getting the profile, I dumped the hives.
***
	$ ./vol.py -f OtterCTF.vmem --profile=Win7SP1x64 hivelist
	Volatility Foundation Volatility Framework 2.6
		Virtual            Physical           Name
		------------------ ------------------ ----
		0xfffff8a00377d2d0 0x00000000624162d0 \??\C:\System Volume Information\Syscache.hve
		0xfffff8a00000f010 0x000000002d4c1010 [no name]
		0xfffff8a000024010 0x000000002d50c010 \REGISTRY\MACHINE\SYSTEM
		0xfffff8a000053320 0x000000002d5bb320 \REGISTRY\MACHINE\HARDWARE
		0xfffff8a000109410 0x0000000029cb4410 \SystemRoot\System32\Config\SECURITY
		0xfffff8a00033d410 0x000000002a958410 \Device\HarddiskVolume1\Boot\BCD
		0xfffff8a0005d5010 0x000000002a983010 \SystemRoot\System32\Config\SOFTWARE
		0xfffff8a001495010 0x0000000024912010 \SystemRoot\System32\Config\DEFAULT
		0xfffff8a0016d4010 0x00000000214e1010 \SystemRoot\System32\Config\SAM
		0xfffff8a00175b010 0x00000000211eb010 \??\C:\Windows\ServiceProfiles\NetworkService\NTUSER.DAT
		0xfffff8a00176e410 0x00000000206db410 \??\C:\Windows\ServiceProfiles\LocalService\NTUSER.DAT
		0xfffff8a002090010 0x000000000b92b010 \??\C:\Users\Rick\ntuser.dat
		0xfffff8a0020ad410 0x000000000db41410 \??\C:\Users\Rick\AppData\Local\Microsoft\Windows\UsrClass.dat
***
Next I used the offsets for \SystemRoot\System32\Config\SAM and \REGISTRY\MACHINE\SYSTEM to dump the password hashes.
***
	$ ./vol.py -f OtterCTF.vmem --profile=Win7SP1x64 hashdump -y 0xfffff8a000024010 -s 0xfffff8a0016d4010 > hashes.txt
***
Awesome! Now I just need to use hashcat to crack the hash for Rick's password. I used [md5decrypt](https://md5decrypt.net/en/Ntlm/#answer) and was able to get the flag.

Flag: CTF{MortyIsReallyAnOtter}
