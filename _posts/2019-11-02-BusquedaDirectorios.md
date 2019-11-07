---
layout: post
title: "Busqueda de Directorios"
subtitle: "Fuerza bruta para encontrar directorios web"
author: "TheusZero"
header-style: text
tags:
  - Enumeracion
  - Web
---

### Busqueda de Directorios Web - |"Dirb"|"Go"|"WFUZZ"|

La busqueda de directorios es una parte fundamental para el desarrollo de una buena enumeracion web, existen variadas formas de concretar una buena enumeracion web, sin embargo existen diferentes metodos y aplicaciones que ayudan a mejorar esta busqueda de directorios.

Las aplicaciones más usadas por mi son Dirbuster, GoBuster y WFUZZ, cada una cumple un rol fundamental en el proceso de busqueda de directorios, ya que de por si son necesarias y me muestran muchas veces cosas que a simple vista no podria haberme percatado

Dirbuster tiene una interfaz virtual, aunque es recomendable lanzar un Dirbuster y un GoBuster a la web.

WFUZZ te sirve para "fuzzear" la web, es decir, encontrar alguna falla de seguridad en la web (SQLinjection o derivadas) de manera que la aplicacion encuentre los directorios importantes y usados de la web.

Existen otras aplicaciones, como extensiones para tu navegador, como lo es:
```vim
wappalyzer
```

>> Recodar estudiar la arquitectura web, existes maquinas como WriteUp que no dejan hacer escaneos por fuerza bruta

### Desde la terminal:

```vim
Dirbuster tiene interfaz grafica pero basta con seleccionar la ip de busqueda y el directorio del diccionario a ocupar

gobuster dir -u "https://www.ip.com/" -w (wordlists)python3 -c "import pty;pty.spawn('/bin/bash')"

wfuzz --hh=24 -c  -w /usr/share/dirb/wordlists/DEFECTO http://ip/.php?FUZZ=test```
