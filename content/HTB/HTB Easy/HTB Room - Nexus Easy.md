#krayin
# Port scan

![[Pasted image 20260723093207.png]]

## Vhost 

10.129.66.158   =>  nexus.htb
10.129.66.158   =>  git.nexus.htb
10.129.66.158   =>  billing.nexus.htb

## Usernames

```
j.matthew j.matthew@nexus.htb
```

## Subdomain Enumeration

- git
- billing

## Enum Data

`APP_NAME='Krayin CRM'`
`DB_HOST=krayin-mysql`
`DB_PORT=3306`
`DB_DATABASE=krayin`
`DB_USERNAME=krayin`
`REDIS_HOST=127.0.0.1`
`REDIS_PASSWORD=null`
`REDIS_PORT=6379`
`MAIL_HOST=mailhog`
`MAIL_PORT=1025`
`MAIL_USERNAME=null`
MAIL_PASSWORD=null`
**`MAIL_FROM_ADDRESS=laravel@krayincrm.com`**
`IMAP_HOST=imap.nexus.htb`
`IMAP_PORT=993`
`IMAP_USERNAME=username1`
**`IMAP_PASSWORD=password1`**
**`DB_PASSWORD=N27xh!!2ucY04`**




## Feroxbuster

```
200      GET        1l      208w     2138c http://git.nexus.htb/assets/img/favicon.svg
200      GET       52l      124w     7604c http://git.nexus.htb/assets/img/favicon.png
303      GET        2l        3w       41c http://git.nexus.htb/explore/ => http://git.nexus.htb/explore/repos
200      GET       31l      384w    22424c http://git.nexus.htb/assets/img/logo.png
200      GET        1l      208w     2138c http://git.nexus.htb/assets/img/logo.svg
200      GET       16l       99w      970c http://git.nexus.htb/api/swagger
200      GET        6l       37w      340c http://git.nexus.htb/.well-known/security.txt
303      GET        2l        3w       49c http://git.nexus.htb/.well-known/change-password => http://git.nexus.htb/user/settings/account
200      GET        1l      576w    19461c http://git.nexus.htb/assets/css/theme-gitea-auto.DGTmr6jR.css
200      GET      290l     1146w    12910c http://git.nexus.htb/user/login
200      GET      339l     1802w    18623c http://git.nexus.htb/explore/repos
200      GET       49l       62w     1183c http://git.nexus.htb/.well-known/openid-configuration
200      GET        5l     2807w   169411c http://git.nexus.htb/assets/js/iife.DYEzIdse.js
200      GET      424l     2210w    22801c http://git.nexus.htb/Admin
200      GET       12l       95w     4340c http://git.nexus.htb/avatars/b17d58524b633e08762e81cb2727e6ee
200      GET        1l     5369w   289155c http://git.nexus.htb/assets/css/index.B_67-OYK.css
200      GET       44l      126w     3551c http://git.nexus.htb/admin.rss
200      GET       50l      115w     3626c http://git.nexus.htb/admin.atom
200      GET      405l     2025w    20257c http://git.nexus.htb/admin/krayin-docker-setup/forks
200      GET      411l     2031w    20436c http://git.nexus.htb/admin/krayin-docker-setup/stars
200      GET      366l     1841w    18621c http://git.nexus.htb/admin/-/projects
200      GET      324l     1681w    17154c http://git.nexus.htb/admin/-/packages
200      GET      424l     2210w    22802c http://git.nexus.htb/admin
200      GET      732l     4328w    46691c http://git.nexus.htb/admin/krayin-docker-setup
200      GET      424l     2210w    22801c http://git.nexus.htb/ADMIN
200      GET       85l    11733w   630676c http://git.nexus.htb/assets/js/index.DesqFkNn.js
200      GET     7505l    56688w  1512643c http://git.nexus.htb/assets/licenses.txt
200      GET      241l     1366w    14472c http://git.nexus.htb/
401      GET        1l        1w       13c http://git.nexus.htb/admin/.git/HEAD
200      GET      424l     2210w    22802c http://git.nexus.htb/admin/
200      GET      732l     4328w    46690c http://git.nexus.htb/admin/krayin-docker-setup/
200      GET      398l     2077w    20610c http://git.nexus.htb/admin/krayin-docker-setup/actions
200      GET      504l     2540w    24919c http://git.nexus.htb/admin/krayin-docker-setup/activity
303      GET        2l        3w       41c http://git.nexus.htb/explore => http://git.nexus.htb/explore/repos
301      GET        2l        3w       58c http://git.nexus.htb/favicon.ico => http://git.nexus.htb/assets/img/favicon.png
200      GET      494l     2816w    26811c http://git.nexus.htb/admin/krayin-docker-setup/compare
303      GET        2l        3w       60c http://git.nexus.htb/issues => http://git.nexus.htb/user/login?redirect_to=%2Fissues
200      GET      504l     2670w    26880c http://git.nexus.htb/admin/krayin-docker-setup/graph
200      GET      735l     3585w    35157c http://git.nexus.htb/admin/krayin-docker-setup/issues
200      GET      428l     2109w    21280c http://git.nexus.htb/admin/krayin-docker-setup/labels
303      GET        2l        3w       67c http://git.nexus.htb/notifications => http://git.nexus.htb/user/login?redirect_to=%2Fnotifications
200      GET      409l     2088w    20960c http://git.nexus.htb/admin/krayin-docker-setup/packages
200      GET      451l     2250w    22451c http://git.nexus.htb/admin/krayin-docker-setup/projects
200      GET        2l        5w      277c http://git.nexus.htb/sitemap.xml
200      GET      425l     2111w    21037c http://git.nexus.htb/admin/krayin-docker-setup/releases
200      GET      444l     2250w    22295c http://git.nexus.htb/admin/krayin-docker-setup/search
303      GET        2l        3w       92c http://git.nexus.htb/admin/krayin-docker-setup/settings => http://git.nexus.htb/user/login?redirect_to=%2Fadmin%2Fkrayin-docker-setup%2Fsettings
303      GET        2l        3w       53c http://git.nexus.htb/admin/krayin-docker-setup/src => http://git.nexus.htb/admin/krayin-docker-setup
401      GET        1l        1w       49c http://git.nexus.htb/v2
200      GET      448l     2205w    21819c http://git.nexus.htb/admin/krayin-docker-setup/tags
405      GET        0l        0w        0c http://git.nexus.htb/admin/krayin-docker-setup/topics
200      GET      393l     2106w    20835c http://git.nexus.htb/admin/krayin-docker-setup/wiki
```


## Krayin Dashboard

Logged in using the creds 

```
j.matthew@nexus.htb
N27xh!!2ucY04
```

![[Pasted image 20260723144635.png]]


## Shell

Found a exploit for verion krayin 2.2.x

![[Pasted image 20260723150745.png]]



## Enumeration for Escalation

Enumerated .env file and find the 

- DB_USERNAME=krayin
- DB_PASSWORD=y27xb3ha!!74GbR

### USED SSH to login as jones 

Found the user flag


# PE [i dont even understand fully] ⭐⭐⭐⭐⭐

```
TOKEN="82b7c49271d73a5c608f4b2856103db56d4c036d"
```

# ITS SO HARD / I DIDNT UNDERSTAND SO I DIDNT DO IT


