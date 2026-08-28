
## Nmap 

```nmap
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.15 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 60:b3:f7:6c:0b:92:ab:00:ac:e7:12:e1:d1:26:9c:1e (ECDSA)
|_  256 c8:30:e6:cb:c6:cd:fc:0c:39:e5:34:04:20:07:b9:b3 (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to http://helix.htb/
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

## Port 80

![[Pasted image 20260826140409.png]]

**Found a vhost**
ContactContact
![[Pasted image 20260826140435.png]]

**Running NIRI**

