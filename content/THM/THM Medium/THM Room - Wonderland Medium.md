
## Posrt Scan

![[Pasted image 20260718094129.png]]

## Port 80

### Gobuster

/img


### Images

![[Pasted image 20260718094501.png]]


### Steg

Hint.txt ===> follow the r a b b i t

in `http://10.48.155.40/r/a/b/b/i/t` ====>  plain text creds

```
alice:HowDothTheLittleCrocodileImproveHisShiningTail
```

## SSH 

![[Pasted image 20260718095434.png]]

Logged in using the creds

![[Pasted image 20260718095504.png]]

- Root is protected by Root
- No write access for warlus*.py

## Import hijakking

Used os lib to get a SHELL as Rabbit


### Rabbit -> Hatter

- Had a executable file name teaParty.sh which had used date command 
- Hijackde the date command by creating and adding the file to the path and changed permissions
- Ran the file and elevated to Hatter

## Hater to ROOT

- Password.txt -> WhyIsARavenLikeAWritingDesk?
- Used Python server to download linpeas.sh
- Found a file with capablity ---> PERL

![[Pasted image 20260718105344.png]]

But the user is not in the Executable group

## Group Changing

```
newgrp hatter
```

Changed the user `hatter` to the group `hatter` 


# ROOT

perl -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/bin/sh"'

```
# whoami 

root
```





