# General Info
## Description
>Let's start easy - whats the PC's name and IP address?
## Solution
This should be easy enough. Let's use volatility to dump the hives.
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
Now we can dump the registry key that will contain the PC name.
***
	$ ./vol.py -f OtterCTF.vmem --profile=Win7SP1x64 printkey -o 0xfffff8a000024010 -K 'ControlSet001\Control\ComputerName\ComputerName'
	Volatility Foundation Volatility Framework 2.6
		Legend: (S) = Stable   (V) = Volatile

		----------------------------
		Registry: \REGISTRY\MACHINE\SYSTEM
		Key name: ComputerName (S)
		Last updated: 2018-06-02 19:23:00 UTC+0000

		Subkeys:

		Values:
		REG_SZ                        : (S) mnmsrvc
		REG_SZ        ComputerName    : (S) WIN-LO6FAF3DTFE***
Done! Now we can find the IP Address using netscan. There's a lot of output so I won't show it, but you will be able to see the IP address 192.168.202.131 show up many times under the local address column.

Flags:
CTF{WIN-LO6FAF3DTFE}
CTF{192.168.202.131}
