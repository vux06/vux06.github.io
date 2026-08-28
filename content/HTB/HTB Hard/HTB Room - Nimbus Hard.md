
### Nmap

```nmap
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 9.6p1 Ubuntu 3ubuntu13.16 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 eb:ab:8f:be:99:02:0b:3e:c4:1c:83:b2:66:2f:17:13 (ECDSA)
|_  256 c1:69:ab:84:f3:88:8b:b3:8a:ae:e2:28:35:54:35:0b (ED25519)
80/tcp open  http    nginx 1.24.0 (Ubuntu)
|_http-server-header: nginx/1.24.0 (Ubuntu)
|_http-title: Nimbus \xE2\x80\x94 Internal Job Scheduler
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

### Port 80

**Home Page**

![[Pasted image 20260814121612.png]]

**Login**

![[Pasted image 20260814121633.png]]

**Job Scheduler**

![[Pasted image 20260814121646.png]]


**Notable Things**

```
- nimbus v1.4.2
- http://nimbus.htb/api/v1/health
- http://nimbus.htb/docs
```

