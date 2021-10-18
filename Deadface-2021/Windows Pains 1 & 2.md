## Windows Pains 1 & 2 - *Forensic*

### - Description ~ Windows Pains 1 -

> One of De Monne's employees had their personal Windows computer 
hacked by a member of DEADFACE. The attacker managed to exploit a 
portion of a database backup that contains sensitive employee and customer PII.
> Inspect the memory dump and tell us the Windows Major Operating System Version, 
bit version, and the image date/time (UTC, no spaces or special characters). 
Submit the flag as flag{OS_BIT_YYYYMMDDhhmmss}.
> Example: flag{WindowsXP_32_202110150900}

> (We were given the link of the download for the file, and the password of it)

### - Solution -

When starting a Memory Forensic Challenge using Volatility, the first step if you
are using Volatility2, is to get the imageinfo of your file, so we have to do the 
following command:
`python vol.py -f ~/CTF/physmemraw imageinfo`

And we get:

![Windows Pains 1](https://user-images.githubusercontent.com/68814228/137789506-977acac3-1c0e-4484-ba5a-29f514826a2f.png)

So we assume that the flag is: flag{Windows10_64_20210907145744}

---

### - Description ~ Windows Pains 2 -

> Using the memory dump file from Window Pains, submit the victim's computer name.
> Submit the flag as flag{COMPUTER-NAME}.

### - Solution -

For this one, we have to use envars, and `grep` the result to only have `"COMPUTERNAME"`
Note: In Volatility on Windows, it would've be a `findstr` instead of `grep`

I've done the following command:
`python vol.py -f ~/CTF/physmemraw --profile=Win10x10941 envars | grep "COMPUTERNAME"`

Result:

![Windows Pains 2](https://user-images.githubusercontent.com/68814228/137793730-08496158-2433-4fe2-8dd0-67217c44a544.png)

So the flag is: flag{DESKTOP-IT8QNRI}
