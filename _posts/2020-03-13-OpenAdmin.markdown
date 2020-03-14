---
layout: post
title: "OpenAdmin"
subtitle: 'HackTheBox - Easy Machine - Linux'
date: 2020-03-13 12:00:00
author: "TheusZero"
header-img: "images/post/OpenAdmin/OpenAdmin.png"
catalog: true
comments: true
tags:
  - Linux
  - Machine
  - Explotations
  - Upgrade
  - Shell
  - Root
  - User
---

# OpenAdmin

## Reconocimiento

#### NMAP

```vim
┌─[zero@parrot]─[~/HTB/Machines/OpenAdmin]
└──╼ $nmap -sC -sV 10.10.10.171 -o nmap.txt
Starting Nmap 7.80 ( https://nmap.org ) at 2020-03-13 19:32 EDT
Nmap scan report for 10.10.10.171
Host is up (0.35s latency).
Not shown: 997 closed ports
PORT    STATE    SERVICE        VERSION
22/tcp  open     ssh            OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 4b:98:df:85:d1:7e:f0:3d:da:48:cd:bc:92:00:b7:54 (RSA)
|_  256 dc:ad:ca:3c:11:31:5b:6f:e6:a4:89:34:7c:9b:e5:50 (ED25519)
80/tcp  open     http           Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
777/tcp filtered multiling-http
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 123.88 seconds
```

#### HTML  

parece ser una pagina de apache comun, asi que mandaremos un burpsuite y un gobuster a ver que podemos encontrar lo sgte:

![](/TheusZero/images/post/OpenAdmin/OpenAdmin1.png)

> gobuster dir -u "http://10.10.10.171/" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o dgobuster.txt
>> /music (Status: 301)
>
>> /artwork (Status: 301)
>
>> /sierra (Status: 301)


