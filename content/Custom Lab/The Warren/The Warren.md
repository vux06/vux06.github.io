#custom-oscp-lab
# Enumeration

## Port Scan

```nmap
PORT      STATE SERVICE
21/tcp    open  ftp
53/tcp    open  domain
80/tcp    open  http
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
1337/tcp  open  waste
2222/tcp  open  EtherNetIP-1
8080/tcp  open  http-proxy
31337/tcp open  Elite
58008/tcp open  unknown
```


## Service and Script Scan

```nmap
PORT      STATE SERVICE     VERSION
21/tcp    open  ftp         vsftpd 2.3.4
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| drwxr-xr-x    3 0        0            4096 Aug 21 07:22 finance
| drwxr-xr-x    5 0        0            4096 Aug 21 07:22 hr
| drwxr-xr-x    4 0        0            4096 Aug 21 07:22 it
| drwxr-xr-x    5 0        0            4096 Aug 21 07:22 logistics
| drwxr-xr-x    2 0        0            4096 Aug 21 07:22 misc
| drwxr-xr-x    2 0        0            4096 Aug 21 07:22 public-notices
|_-rw-r--r--    1 0        0             325 Aug 21 07:22 welcome.txt
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 192.168.122.1
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.5 - secure, fast, stable
|_End of status
53/tcp    open  domain      ISC BIND 9.20.26-1 (Debian Linux)
| dns-nsid: 
|_  bind.version: 9.20.26-1-Debian
80/tcp    open  http        Apache httpd 2.4.68 ((Debian))
|_http-server-header: Apache/2.4.68 (Debian)
| http-git: 
|   192.168.122.14:80/.git/
|     Git repository found!
|     .git/config matched patterns 'user'
|     Repository description: Unnamed repository; edit this file 'description' to name the...
|_    Last commit message: rotated, see vault. 
| http-robots.txt: 8 disallowed entries 
| /admin/ /backup/ /old/ /dev/ /test/ /warren/ /internal/ 
|_/carrot-cms/
|_http-title: Home \xE2\x80\x94 CarrotMart
139/tcp   open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: LAPINLOGISTICS)
443/tcp   open  ssl/http    Apache httpd 2.4.68
|_http-title: Apache2 Default Page
|_http-server-header: Apache/2.4.68 (Debian)
| tls-alpn: 
|_  http/1.1
| ssl-cert: Subject: commonName=internal.lapinlogistics.local/organizationName=Lapin Logistics/countryName=GB
| Subject Alternative Name: DNS:internal.lapinlogistics.local
| Not valid before: 2026-08-21T07:22:37
|_Not valid after:  2036-08-18T07:22:37
|_ssl-date: TLS randomness does not represent time
445/tcp   open  netbios-ssn Samba smbd 4.24.5-Debian-4.24.5+dfsg-1 (workgroup: LAPINLOGISTICS)
1337/tcp  open  http        Gunicorn
|_http-title: Lapin Logistics \xE2\x80\x94 Golden Carrot Submission
|_http-server-header: gunicorn
2222/tcp  open  ssh         OpenSSH 10.4p1 Debian 4 (protocol 2.0)
8080/tcp  open  http        Apache httpd 2.4.68 ((Debian))
|_http-title: Lapin Logistics \xE2\x80\x94 Marketing &#8211; Just another WordPress site
|_http-server-header: Apache/2.4.68 (Debian)
|_http-open-proxy: Proxy might be redirecting requests
|_http-generator: WordPress 5.7.2
31337/tcp open  Elite?
| fingerprint-strings: 
|   DNSStatusRequestTCP: 
|     IUCwoMvWTVMu480xmD+I3rk42CTT4swTyqRE6OsorQzdVn+pBOEYtIEuNxCgoEBE
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|     Connection closed by foreign host.
|   DNSVersionBindReqTCP: 
|     3BAzDCFMjqP8QoHuUopaV/9YiZeDixr5lPnf6rr+GhQR4pRmvJugZ+jbuS+mLu6H
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|     Connection closed by foreign host.
|   GenericLines: 
|     ySATHDMdvNHt8UdWDXRXgqQFQo8MCxpE4kwluwSL98CKW3sX/SXUkUivSYT3ZbdE
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|     Connection closed by foreign host.
|   GetRequest: 
|     OuDfzgYK7H3zexO7/Batt3BYJA+/TyDew2ILuAJMUaZ9uOILmieoB+z+8DqKI+yI
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|     Connection closed by foreign host.
|   HTTPOptions: 
|     i5mELGmOlo+hS01Xn65wrV6gDS1iEjI0lz9RVdosoSrp+fiC6AhQ6Eiek4dzDxYe
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|     Connection closed by foreign host.
|   Help: 
|     6B1wwhEywft+kHxnrdwyHnF02vm24im0JiueoI5uAZFy0BuBr0XvATi5D4ov0X5b
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|     Connection closed by foreign host.
|   NULL: 
|     ESe5wzgoDMWBB8jfVG2Z4nCM2mSKfkruPGGL+4O9C7Si/NgDxrSPaYDKXf6UXSFu
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|     Connection closed by foreign host.
|   RPCCheck: 
|     rlrMqhYFsvB9Vy+JJYKSnp47q7KKZ4bbpsrJumMTJVPjBMptknh5yG7G8mcammmx
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|     Connection closed by foreign host.
|   RTSPRequest: 
|     SeWGjZjN1PS4dD5CxVu6RL1ZGhJQVBVTgNF4cK2NY6+N+G06FhgSUsfMiSZRzLG5
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|     Connection closed by foreign host.
|   SIPOptions: 
|     /CuePDt+dETGjAMBKXtcHjdZUFvQw2+3V7jvDcBvD+Gt+ZHzpjkQTOlrSk3XKGx+
|     BurrowD v1.4.2-stable (Lapin Logistics internal)
|_    Connection closed by foreign host.
58008/tcp open  http        Gunicorn
|_http-server-header: gunicorn
| http-title: Sign in \xC2\xB7 The Warren
|_Requested resource was /login

Host script results:
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.24.5-Debian-4.24.5+dfsg-1)
|   Computer name: kali
|   NetBIOS computer name: LAPIN-SRV\x00
|   Domain name: 
|   FQDN: kali
|_  System time: 2026-08-21T03:44:23-04:00
|_clock-skew: mean: 1h20m00s, deviation: 2h18m34s, median: 0s
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-time: 
|   date: 2026-08-21T07:44:23
|_  start_date: N/A
| smb2-security-mode: 
|   3.1.1: 
|_    Message signing enabled but not required
|_nbstat: NetBIOS name: LAPIN-SRV, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
```

## Port 21

**Anonymous Login worked**

![[Pasted image 20260822170357.png]]

