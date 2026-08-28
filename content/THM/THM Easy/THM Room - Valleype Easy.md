
## Nmap

![[Pasted image 20260721105938.png]]

## Directory Enum

```
.hta                 (Status: 403) [Size: 278]
.htaccess            (Status: 403) [Size: 278]
.htpasswd            (Status: 403) [Size: 278]
gallery              (Status: 301) [Size: 316] [--> http://10.48.141.132/gallery/]
index.html           (Status: 200) [Size: 1163]
pricing              (Status: 301) [Size: 316] [--> http://10.48.141.132/pricing/]
server-status        (Status: 403) [Size: 278]
static               (Status: 301) [Size: 315] [--> http://10.48.141.132/static/]
```


Found `http://10.48.141.132/pricing/note.txt`

```
J,
Please stop leaving notes randomly on the website
-RP
```

Found another note at `http://10.48.141.132/static/00`                                                                     ⭐

```
dev notes from valleyDev:
-add wedding photo examples
-redo the editing on #4
-remove /dev1243224123123
-check for SIEM alerts
```


## Creds in Code

```
view-source:http://10.48.141.132/dev1243224123123/dev.js

loginButton.addEventListener("click", (e) => {
    e.preventDefault();
    const username = loginForm.username.value;
    const password = loginForm.password.value;

    if (username === "siemDev" && password === "california") {
        window.location.href = "/dev1243224123123/devNotes37370.txt";
    } else {
        loginErrorMsg.style.opacity = 1;
    }
})
```


```
dev notes from valleyDev:
-add wedding photo examples
-redo the editing on #4
-remove /dev1243224123123
-check for SIEM alerts
```

## Found Creds in FTP

```
POST /index.html HTTP/1.1

Host: 192.168.111.136

User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:102.0) Gecko/20100101 Firefox/102.0

Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8

Accept-Language: en-US,en;q=0.5

Accept-Encoding: gzip, deflate

Content-Type: application/x-www-form-urlencoded

Content-Length: 42

Origin: http://192.168.111.136

Connection: keep-alive

Referer: http://192.168.111.136/index.html

Upgrade-Insecure-Requests: 1

  

uname=valleyDev&psw=ph0t0s1234&remember=on
```


## SSH

- Logged im as ValleyDev with the above creds
- Found a File named valleyAuthenticator
- Downloaded to my machine
- Used UPX to DEUbfuscation
- Found MD5 hashes , cracked `valley:liberty123`
- Logged in as valley in ssh

# Root

Found a Cron job that runs as root, modified base64.py to get root access.