---
layout: post
title: "CheatSheets"
author: "TheusZero"
subtitle: 'Codigos mas usados'
header-img: "images/Sekiro3.png"
catalog: true
comments: true
---
## Linux

#### Sudo 

```Python
sudo -l
```

```Python
sudo -u USER /bin/bash
```

```Python
sudo -u USER commandLine /dir/file
```
#### Net
```Python
sockstat -4 -l 
```
```Python
netstat -anp tcp | grep -i listen
```
#### DNS

**add the dns server to your machine**

```Python
echo "Mensaje" | sudo tee -a /dir/archivo 
```

#### Echo

**escribir sin vim**
```Python
echo “Reverse shell” > /dir/file
```
#### Perl

```Python
sudo perl -e 'exec "/bin/sh";
```
#### SSH

**El punto tambien va del final.**
```Python
sshpass -p 'passwordOfUser' scp -oStrictHostKeyChecking=no User@IP:File .
```

**Port Forwarding Desde mi maquina**
```Python
ssh -L port:127.0.0.1:port -N -f -l userSSH IP 
```

**ssh-passwd fuerza bruta (John)**

```Python
/JohnTheRipper/run/ssh2john.py id_rsa > forjohn.txt
/JohnTheRipper/run/john forjohn.txt --wordlist=/dir/wordlist.txt
```

**ssh-passwd-user fuerza bruta (Hydra)**

```Python
hydra -l 'user' -P /dir/wordlist ssh://IP 
```

#### Python
**Upgrade Reverse Shell**
```Python
python3 -c "import pty;pty.spawn('/bin/bash')"
```
**Simple Web Server**
```Python
python2 -m SimpleHTTPServer 4567
```
#### Binaries

**Recordar jugar con las SUID para escalar privilegios con ayuda de GTFObins**

```Python
find / perm -u=s -type f 2>/dev/null
```
```Python
find / -user root -perm -4000 -print 2>/dev/null
```
```Python
find / -user root -perm -4000 -exec ls -ldb {} \;
```
#### Others
**Another way to read a file**
**read a single file**
```Python
echo < archive.txt
while read line; do echo $line; done < archivo.txt
```
```Python
grep . archivo.txt
```
**read all files**
```Python
grep -R .
```

## Windows

## Link Interesantes

> [GTFOBins](https://gtfobins.github.io/)

> [ReverseShellsPM](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

> [ExploitDB](https://www.exploit-db.com/)

> [Campo de Marte](https://www.campodemarte.cl/)

> [CTFtime](https://ctftime.org/)

> [Escritura Exploits (Español)](https://fundacion-sadosky.github.io/guia-escritura-exploits/)

> [escapar de shells restringidas](https://www.hackplayers.com/2018/05/tecnicas-para-escapar-de-restricted--shells.html)

> [Basic Linux Privilege Escalation](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/)

> [Windows Privilege Escalation Fundamentals](http://www.fuzzysecurity.com/tutorials/16.html)

> [Malla-Interactiva-USM](https://mallas.labcomp.cl/?m=TEL)

> [Lab-Redes](http://www2.elo.utfsm.cl/~tel241/20102s/)

## Herramientas
> [PsPy](https://github.com/DominicBreuker/pspy) 

> [LinEnum](https://github.com/rebootuser/LinEnum/)

> [PsPy64](https://f4d3.io/assets/downloads/linux/pspy64s) (grax f4d3 :D)

> []()