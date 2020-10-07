---
layout: post
title: "Sistemas Operativos"
subtitle: 'Resumen de clases, libros y apuntes USM'
date: 2020-09-18 12:00:00
author: "TheusZero"
header-img: "images/post/SistemasOperativos/1.jpg"
catalog: true
comments: true
tags:
  - Programacion
  - USM
  - Tareas
  - Linux
  - Windows
---

## Links Importantes

## Clases

**clase 1**

#### Que es un Sistema operativo

es el programa que administra el hardware del computador, dandole una base para aplicaciones y actua de intermediario entre el usuario y el hardware

#### componentes basicos de la maquina:

> Hardware
>> CPU, memoria, I/O devices
> Sistema operativo
>> controla y cordina cada uno del hardware para hacer de intermediario entre el usuario y la maquina
> Aplicaciones y programas
>> aplicaciones y softwares 
> Usuarios
>> personas, compiladores, web browsers, etc.

![](/TheusZero/images/post/SistemasOperativos/2.png)

#### que hacen los sistemas operativos

> desde **la vista del usuario** son designados para un facil uso de la maquina.

> desde **la vista del sistema** el sistema operativo realiza de **administrador de recursos**
>> de esa manera administra el CPUtime, el espacio de memoria, la cantidad de almacenamiento del sistema.
>
>> frente a los conflictos que puede presentar la maquina, el sistema operativo decidira que hacer para alojar memoria o recursos a programas especificos para el usuario. 

cuando estamos iniciando el computador, este correra un programa inicial, que sera llamado **bootstrap program** esto esta ubicado en una memoria (ROM) o en su defecto un (EEPROM) que es lo mismo pero sera electricamente programable. ambos seran solo para lectura en el hardware.
Este inicializa los registros de la CPU, de los controladores de los dispositivos  y de el contenido en memoria.

> el **bootstrap program** debe localizar el sistema operativo **kernel** y cargarlo en la memoria

los programas del sistemas son cargados tambien al momento en el que inicia el sistema

#### como se inician los elementos de un sistema operativo

>> I/O devices y the CPU pueden ejecutarse al mismo tiempo (son unidades autonomas)
>
>> cualquier controlador de dispositivo que esta acargo de un dispositivo especifico
>
>> cualquier controlador de dispositivo que tenga buffers locales
>
>> la CPU mueve datos desde o hacia la memoria principal hacia los buffers locales
>
>> I/O is from the device to local buffer of controller
>
>> los controladores de dispositivos informa a la CPU si alguna operacion ha terminado o ha sido interrumpida

![](/TheusZero/images/post/SistemasOperativos/3.png)

#### funciones comunes o interrupciones

las interrupciones se pueden generar tanto por el hardware como por el software
cuando son generadas por el software recibe el nombre de **trap** o **exception** y se ejecutan operaciones especiales que son denominadas **llamadas a sistema** o **system calls**

cuando la CPU es interrumpida, esta detiene lo que sea que este haciendo e
inmediatamente transfiere la ejecucion a un lugar para arreglarla

> la localizacion que arregla esto usualmente contiene la direccion de partida donde esta el servicio de rutina, este se ejecuta y atiende la interrupcion, cuando esta termina la CPU vuelve a su trabajo.
>> esta interrupcion debe ser arreglada super rapido

> existe un numero definido de interrupciones que son posibles, esta es llamada **table of pointers** y son las que interrupen el servicio de rutinas que se son usadas.

> la tabla de de punteros (**table of pointers**) es almacenada en la baja memoria (son las primeras cien locaciones) que son llamadas vectores de interrupcion

#### Interrupt Timeline (Linea de tiempo de interrupciones)

![](/TheusZero/images/post/SistemasOperativos/4.png)

#### Storage Structure (estructura de almacenaje)

la cpu puede cargar instrucciones solo desde la memoria principal (RAM), por lo que cualquier programa
que se ejecute debe ser almacenado allí

> Computers use other forms of memory as well (cache memory, CDROM, etc)

la memoria para nosotros seran un array de bytes, donde **cada bite tiene su propia direccion**

la carga de instrucciones mueven bytes desde la memoria principal hacia la CPU, tenemos los registros **stores** que son instrucciones que mueven el contenido de un registro (CPU) a la memoria principal

**Idealmente** nosotros queremos que los programas y datos que estan en la memoria principal permanentemente, pero eso no es posible por lo siguiente:

> la memoria principal es muy chica (small) para guardar todos los programas que necesitamos y la data (para guardarlos permanentemente) 
>
> la memoria principal es un almacenamiento **volatil** que pierde su contenido cuando es apagado

muchos sistemas de computadoras proveen un almacenamiento securndario que son extensiones de la memoria principal

la memoria principal requiere de este almacenamiento secundario que es capaz de contener un monton de largas cantidades de datos

el almacenamiento secundario mas comun es el disco magnetico (disco Duro)

Las principales diferencias entre los distintos sistemas de almacenamiento radican en la velocidad, costo, size y la volatilidad

La amplia variedad de sistemas de almacenamiento se puede organizar en una jerarquía.
según velocidad y coste. Los niveles superiores son caros, pero
son rapidos.

![](/TheusZero/images/post/SistemasOperativos/5.png)

#### I/O Structure

una gran parte del codigo del sistema operativo es dedicado para administrar el I/O, debido a su importancia para la confiabilidad y el desempeño de un sistema

Un sistema informático tiene como propósito general que la CPU y los múltiples
controladores de dispositivos que esten conectados a través de un bus común.
>> Cada controlador de dispositivo está a cargo de un tipo específico de dispositivo.
>
>> Se encarga de mover los datos entre los dispositivos periféricos que controla y su almacenamiento intermedio local.

Normalmente, los sistemas operativos tienen un controlador de dispositivo para cada dispositivo.

> Este controlador de dispositivo proporciona al sistema operativo una interfaz al dispositivo.

para iniciar una operacion de entrada y salida (I/O), el dispositivo carga apropiadamente los registros locales del dispositivo controlador

 el controlador de disposistivos examina el contenido que este registra para determinar que accion tomar
 
> el controlador comienza a transferir data desde el dispositivo a su buffer local
>
> una vez tranferida la data completa, el controlador de dispositivos informa al 

## Ejercicios Importantes

## Libro

