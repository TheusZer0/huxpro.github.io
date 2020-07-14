---
layout: secret_post
title: "Upgrade Reverse Shell"
subtitle: 'Para root-users con python'
author: "TheusZero"
header-style: text
key:"Hola"
tags:
  - Root
  - User
  - Explotations
  - Upgrade
  - Shell
---

Una vez ya obtenida alguna shell del user o del root, ya sea como www-data o alguna otra, muchas veces ocurren errores al tratar de ejecutar comandos variados, debido a que la shell que se obtiene es “feisima” y se bugea en la terminal.

Debido a esto, existen comandos para poder “upgradear” la shell obtenida, de manera que asi puedes tener una mejor vision y uso de la terminal. Los comandos no se te van a “bugear” tanto (vi siempre se bugea uwu), pero por lo demas es necesario y hasta obligatorio.

### Para hacerlo con Python:

```vim
python3 -c "import pty;pty.spawn('/bin/bash')"
```







