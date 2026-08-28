
## Vuxscan

```
=== vuxScan results for 10.129.68.206 ===
10.129.68.206    21     open
10.129.68.206    22     open
10.129.68.206    80     open
```

## Users

- Nathan
## Nmap

Nothing Usefull
## Port 80

![[Pasted image 20260725165215.png]]


**Found a pcap file Downloader**

- Downloaded a 0.pcap file using **IDOR**


## Creds for FTP

- User : nathan
- Passwd : Buck3tH4TF0RM3!

![[Pasted image 20260725221440.png]]


## Ftp 

Logged in to FTP and Got the user.txt

## SSH

- Used the same creds to login to SSH
- Enumerated potential things for PE
- USed Linpease
# PE

- Found python has some capabilities
- cap_setuid,cap_net_bind_service+eip
- **Can change UIDs**

```
import os
os.setuid(0)
os.system("/bin/bash")


root@ubuntu# 
```


