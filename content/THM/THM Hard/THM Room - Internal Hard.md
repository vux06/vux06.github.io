

### Host name change

10.48.163.134 -> internal.thm

# Port scan

![[Pasted image 20260710141029.png]]

# Port 80 

Default Apache page.
**Apache/2.4.29** 

### Curl

curl -I http://10.48.163.134/
HTTP/1.1 200 OK
Date: Fri, 10 Jul 2026 08:43:37 GMT
Server: **Apache/2.4.29** (Ubuntu)
Last-Modified: Mon, 03 Aug 2020 01:49:20 GMT
Accept-Ranges: bytes
Content-Length: 10918
Vary: Accept-Encoding
Content-Type: text/html

![[Pasted image 20260710141239.png]]


## Directory Fuzzing

blog                 (Status: 301) [Size: 313] [--> http://10.48.163.134/blog/]
wordpress            (Status: 301) [Size: 318] [--> http://10.48.163.134/wordpress/]
javascript           (Status: 301) [Size: 319] [--> http://10.48.163.134/javascript/]
phpmyadmin           (Status: 301) [Size: 319] [--> http://10.48.163.134/phpmyadmin/]

### /Blog/ fuzzing

index.php            (Status: 301) [Size: 0] [--> http://10.48.163.134/blog/]
***wp-admin             (Status: 301) [Size: 322] [--> http://10.48.163.134/blog/wp-admin/]***
***wp-content           (Status: 301) [Size: 324] [--> http://10.48.163.134/blog/wp-content/]***
***wp-includes          (Status: 301) [Size: 325] [--> http://10.48.163.134/blog/wp-includes/]***
**xmlrpc.php**           (Status: 405) [Size: 42]

## Files Fuzzing

index.html              [Status: 200, Size: 10918, Words: 3499, Lines: 376, Duration: 50ms]
.htaccess               [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 84ms]
.                       [Status: 200, Size: 10918, Words: 3499, Lines: 376, Duration: 57ms]
.html                   [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 74ms]
.php                    [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 82ms]
.htpasswd               [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 72ms]
.htm                    [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 54ms]
.htpasswds              [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 72ms]
.htgroup                [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 76ms]
wp-forum.phps           [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 74ms]
***.htaccess.bak           [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 58ms**]*
.htuser                 [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 75ms]
.ht                     [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 94ms]
.htc                    [Status: 403, Size: 278, Words: 20, Lines: 10, Duration: 101ms]


## WPScan

XML-RPC seems to be enabled: http://10.48.163.134/wordpress/xmlrpc.php
WordPress readme found: http://10.48.163.134/wordpress/readme.html
WordPress version 5.4.2 identified (Insecure, released on 2020-06-10)

#### WP Plugins

akismet
 | Location: http://10.48.163.134/wordpress/wp-content/plugins/akismet/
 | Latest Version: 5.7


### XMLRPC Brute Force (Learnt Today)

Found passwd admin:my2boys


## Wordpress Access

- Got into the Dashboard.
- Opened Theme Editor
- Edited 404.php page with a php revshell
- opened internal.thm/ 404
- Got the revshell

![[Pasted image 20260710170007.png]]


## PhpMyAdmin

cat /var/www/html/wordress/config.php

Found the DB data:

- Username : wordpress
- Password : wordpress123
- DB_Name : wordpress


## /opt  (used writeup for a sec)

- Found a file that say

- aubreanna:bubb13guM!@#123

- `Escalated as Aubreanna`


## Jenkins 

Jenkins running in the internal ip on port 8080

Used _**Chisel**_ to Port Forward (Tunnel) to make it external 

Bruteforced the Creds

Got the access to Jenkins console as admin


## Root flag

REVSHELL from the Jenkins Console

Cat note.txt in jenkins@jenkins

Got the root creds