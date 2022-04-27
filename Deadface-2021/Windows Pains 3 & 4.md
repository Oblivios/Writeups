## Windows Pains 3 & 4 - *Forensic*

### - Description ~ Windows Pains 3 -

> Using the memory dump file from Window Pains, find out the name of the malicious process.
> Submit the flag as flag{process-name_pid} (include the extension).
> Example: flag{svchost.exe_1234}

### - Solution -

To find the malicious process, we're gonna use the plugin of volability called "malfind".

`python vol.py -f ~/CTF/physmemraw -profile=Win10x64_19041 malfind`

![Windows Pains 3 Malfind](https://user-images.githubusercontent.com/68814228/137811296-34c7b478-e815-4d31-bfae-ce6bc02f136b.png)

It returns to us something like 8/9 processes, but we can see that there's the one who's there 5 times, which is userinit.exe, who seems suspicious.
So now, what we have to do is dump this process (get a look to the screen of Windows Pains 4), to get it to our machine, and analyze it with VirusTotal.

![Windows Pains 3 Malicious](https://user-images.githubusercontent.com/68814228/137811286-c4dfe538-95ee-4078-8f02-0dc5da35b493.png)

Then, we analyze this executable, by putting it on VirusTotal, and we can clearly see that this is the malicious process.

![Windows Pains 3 VirusTotal](https://user-images.githubusercontent.com/68814228/138442279-31333bc3-92f8-4114-83d1-185df56cb876.png)

So we assume that the flag is: flag{userinit.exe_8180}

---

### - Description ~ Windows Pains 4 -

> We want to see if any other machines are infected with this malware. Using the memory dump file from Window Pains, 
submit the SHA1 checksum of the malicious process.
> Submit the flag as flag{SHA1 hash}.
> CAUTION Practice good cyber hygiene! Use an isolated VM to download/run the malicious process. While the malicious process is relatively benign, if you're using an insecurely-configured Windows host, it may be possible for someone to compromise your machine if they can reach you on the same network.

### - Solution -

This one was free points if you had solved Windows Pains 3, because all you have to do is dump the process of the malicious process with the following command:
`python vol.py -f ~/CTF/physmemraw --profile=Win10x64_19041 procdump -D . -p 8180`

![Windows Pains 4 Proc](https://user-images.githubusercontent.com/68814228/137811313-b9c04796-d965-4a0c-bbf1-9e1cdd58633d.png)

And then, get the sha1 of the executable, with:
`sha1sum executable.8180.exe`

![Windows Pains 4 SHA1](https://user-images.githubusercontent.com/68814228/137811304-51314dc2-31d3-46f6-88dd-5b4e7c00fe3b.png)

So the flag is: flag{905706378eb21d925a411784ff65f22d15fea033}
