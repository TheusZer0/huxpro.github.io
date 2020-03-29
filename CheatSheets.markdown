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

#### DNS

```vim
echo "10.10.10.29 bank.htb" | sudo tee -a /etc/host 
```
```vim
echo “10.10.10.29 bank.htb ” > /etc/hosts
```

#### Echo
```vim
echo “Reverse shell” > /dir/file
```
#### Perl

```vim
sudo perl -e 'exec "/bin/sh";
```
## Windows

## Link Interesantes

> [GTFOBins](https://gtfobins.github.io/)

> [ReverseShellsPM](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

> [ExploitDB](https://www.exploit-db.com/)

> [Campo de Marte](https://www.campodemarte.cl/)

> [CTFtime](https://ctftime.org/)

> [Escritura Exploits (Español)](https://fundacion-sadosky.github.io/guia-escritura-exploits/)