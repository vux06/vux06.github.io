
## Nmap

![[Pasted image 20260719145440.png]]


## Username Found

scr1ptkiddy  =>  project manager on Silverpeas

## Directory Enumeration

![[Pasted image 20260719150617.png]]


/silverpeas => From hint

##  Cewl && Burp

Used Cewl to create custom wordlists and used burp for brute forcing web login form in the silverpes endpoint.

And found out the passwd is scr1ptkiddy:adipiscing


## Silverpeas Dashboard

- Found an IDOR on the notificatiosn and found the creds for SSH `tim:cm0nt!md0ntf0rg3tth!spa$$w0rdagainlol`
- Logged in to ssh

# PE

- Same group lead to read of ` cat /var/log/auth.log* | grep -i tyler `
- Got the creds` tyler:_Zd_zx7N823/`
- SSH logged in
- sudo -l reveals ALL (ALL:ALL)
- Root flag obtained

