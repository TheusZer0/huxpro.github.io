---
layout: post
title: "Reverse Engineering - TryHackMe"
subtitle: 'TryHackMe - Hacktivities - First ReverseEngineering'
date: 2020-05-25 12:00:00
author: "TheusZero"
header-img: "images/post/Reverse/portada.png"
catalog: true
comments: true
tags:
  - Programacion
  - Linux
  - Machine
  - Explotations
  - Upgrade
  - Shell
  - Root
  - User
  - Reverse Engineering
---

# Reverse Engineering - TryHackMe - Hacktivities

Este es el primer WriteUp de TryHackMe que hago, esta enfocado a la ingenieria reversa, un campo de la ciberseguridad que no domino para nada y que me encantaria aprender.

Por ello, en este WriteUp intentare anotar lo mas posible sobre lo que voy aprendiendo.

**Recordatorio**
> Hay muchas cosas que no se, por lo que si hay algo que esta malo o es muy obvio me disculpan. Gracias!

## CrackMe1
 
#### Reconocimiento

lo primero que hice fue bajar el archivo, obviamente sabia que era un desafio de reverse pero de todas maneras nunca esta de mas hacer un **File**.

![](/TheusZero/images/post/Reverse/crackme1_2.png)

ejecutando el binario nos muestra lo sgte: 

![](/TheusZero/images/post/Reverse/crackme1_2.png)

haciendo un rec basico, usando **strings** pude identificar altiro la contraseña siendo el string extraño que no tiene explicacion.

![](/TheusZero/images/post/Reverse/crackme1_3.png)

> hax0r

#### IDA


