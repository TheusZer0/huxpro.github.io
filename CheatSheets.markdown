---
layout: post
title: "CheatSheets"
author: "TheusZero"
subtitle: 'Codigos mas usados'
header-img: "images/footer-cover6.png"
catalog: true
comments: true
---
## Linux

#### Sudo 

```vim
sudo -l
```

```vim
sudo -u USER /bin/bash
```

```vim
sudo -u USER commandLine /dir/file
```
#### Net
```vim
sockstat -4 -l 
```
```vim
netstat -anp tcp | grep -i listen
```
#### DNS

```vim
echo "Mensaje" | sudo tee -a /dir/archivo 
```
```vim
echo “Mensaje” > /dir/archivo
```

#### Echo
```vim
echo “Reverse shell” > /dir/file
```
#### Perl

```vim
sudo perl -e 'exec "/bin/sh";
```
#### SSH
> el punto tambien va del final.
```vim
sshpass -p 'passwordOfUser' scp -oStrictHostKeyChecking=no User@IP:File .
```
> Port Forwarding Desde mi maquina
```vim
ssh -L port:127.0.0.1:port -N -f -l userSSH IP 
```
#### Binaries
```vim
find / perm -u=s -type f 2>/dev/null
```
## Windows

## Link Interesantes

> [GTFOBins](https://gtfobins.github.io/)

> [ReverseShellsPM](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

> [ExploitDB](https://www.exploit-db.com/)

> [Campo de Marte](https://www.campodemarte.cl/)

> [CTFtime](https://ctftime.org/)

> [Escritura Exploits (Español)](https://fundacion-sadosky.github.io/guia-escritura-exploits/)

## Herramientas
> [PsPy](https://github.com/DominicBreuker/pspy) 
>
> [LinEnum](https://github.com/rebootuser/LinEnum/)
>
> [PsPy64](https://f4d3.io/assets/downloads/linux/pspy64s) (grax f4d3 :D)
>
> []()