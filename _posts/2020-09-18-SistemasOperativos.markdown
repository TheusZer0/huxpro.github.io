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
> una vez tranferida la data completa, el controlador de dispositivos informa al device driver con un **interrupt**

de esta forma el interrupt-driver I/O es bueno para mover pequeñas cantidades de datos pero se 

para resolver este problema, se usa la memoria de acceso directo (DMA).

> el controlador de dispositivos transfiere un bloque entero de data directamente hacia o desde su buffer de almacenamiento para la memoria, sin intervencion de la CPU

> mientras el controlador de dispositivos esta ejecutando estas operaciones, la CPU esta disponible para realizar otro trabajo.

![](/TheusZero/images/post/SistemasOperativos/6.png)

#### Storage Definitions and Notation Review (definicion de almacenamientos y revision de notaciones)

la unidad basica del almacenamiento computacional es el bit. el bit puede contener uno dos valores (0,1). Todos los otros almacenamientos en la computadora estan
basados en colleciones de bits. es asombroso como algunas cosas el computador puede representar como:

> numbers, letters, images, movies, sounds, documents, and programs, to name

un **byte** es de 8bits, y en la mayoría de las computadoras es el más pequeño y conveniente cantidad de almacenamiento.

![](/TheusZero/images/post/SistemasOperativos/7.png)

#### Computer-System Architecture (arquitectura de los sistemas computacionales)

Single-Processor Systems: una CPU principal capaz de ejecutar un proposito general. (multi-proposito)

Multi-Processor (multi-core) System: muchos sistemas actuales tienen dos o mas procesadores, donde cada uno de estos tiene muchos cores y comparten el clock y la memory.

los sistemas multiprocesadores tienen 3 ventajas principales:

> rendimiento incrementado
>> mas trabajo hecho en menos tiempo.

> Economy of scale. Multiprocessor systems can cost less than equivalent multiple single-processor systems

> mas confiable:
>> el fallo de un procesador no detendra el sistema solo lo volvera mas lento.

los sistemas multi-procesador tienen 2 tipos:

> Multiprocesador Asimetrico: cada procesador es asignado a una tarea en especifica
>> este esquema define una relacion jefe-trabajador. El procesador jefe asigna el trabajo a los procesadores trabajadores

> Multiprocesador simetrico: cada procesador realiza todas las tareas
>> todos los procesadores son companeros, cada uno de los procesadores tiene su propio set de registros, asi como un cache privado o local. Sin embargo todos los procesadores comparten memoria fisica. 
>
>> el beneficio de este modelo es que muchos procesos pueden correr simultaneamente- N procesadores pueden correr si hay N CPUs 

**Symmetric Multiprocessing Architecture**
![](/TheusZero/images/post/SistemasOperativos/8.png)

#### A Dual-Core Design

> Multi-chip and multicore

> una tendencia reciente en el diseno de la CPU es incluir multiples cores en un solo chip

> estos sistemas multiprocesador son llamados multi-cores. Pueden ser mas eficientes que multiples chips esten en un solo core,
> debido que la comunicacion dentro de un chip es mas rapida que la comunicacion entre distintos chips. 

ademas un chip con multiples cores usas significativamente menos poder que varios chips con un solo core cada uno.

> en este diseno, cada core tiene propio registro y su propio cache local. Otro diseno pueden usar cache compartido o una combinacion entre cache locales y compartidos.

> These multicore CPUs appear to the operating system as N standard processors

![](/TheusZero/images/post/SistemasOperativos/9.png)

uno de los aspectos mas importante de los sistemas operativos es la habilidad multi-programa

> multiprogramar aumenta la utilizacion de la CPU organizando los trabajos (code and data) ya que la CPU siempre tiene uno que ejecutar

la idea es la siguiente:

> el sistema operativo mantiene varios trabajos simultáneamente en la memoria
>
> ya que la memoria principal es muy pequena para atribuirse todos los trabajos, los trabajos se mantienen 
>inicialmente dentro del disco en el **job pool**

> el **job pool** consiste en que todos los procesos que residen en el disco 
>estan esperando a ser acomodados en la memoria principal

> el sistema operativo elige y empieza a ejecutar uno de los trabajos en la memoria

> evenutalmente el **job pool** debe esperar alguna tarea, asi como una operacion I/O para completarse. en un sistema multi-programable, el sistema operativo simplemente cambia y ejecuta otro trabajo

**the CPU is never idle**

![](/TheusZero/images/post/SistemasOperativos/10.png)

el **time sharing** o **multitasking** es una esxtension logica del multiprogramming

> La CPU ejecuta varios trabajos cambiando entre ellos, pero Los cambios ocurren con tanta frecuencia que los usuarios pueden interactuar con cada programa mientras se está ejecutando.

> un sistema operativo a tiempo compartido aloja muchos usuarios que comparten el computador simultaneameente
>> esto provee una pequena porcion de computador de tiempo-compartido a cada usuario **cuentas diferentes**

> un programa carga dentro de la memoria y ejecuta lo que se llama un proceso. cuando el proceso se ejecuta,
>esto tipicamente ejecuta, generalmente ejecuta esto por un solo corto tiempo antes de que finalice o necesite ejecutar una I/O.

> el tiempo compartido **time sharing** y el multiprograming requieren que se mantengan varios trabajos simultáneamente en la memoria

> si varios trabajos estan listos para ser traidos a la memoria y si no hay suficiente espacio en disco para todos ellos, entonces el sistema debe escoger entre estos. **Esto implica la programación de trabajos, job scheduling**

Tener varios programas en la memoria al mismo tiempo requiere alguna forma
de la gestión de la memoria

Si varios trabajos están listos para ejecutarse al mismo tiempo, el sistema debe elegir
qué trabajo se ejecutará primero. Tomar esta decisión es programar la CPU


Memoria virtual

> esta es una técnica que permite la ejecución de un proceso que no es completamente en la memoria

> Permite a los usuarios ejecutar programas que son más grandes que la memoria fisica.

> Además, abstrae la memoria principal en una matriz grande y uniforme de almacenamiento

Un sistema de tiempo compartido también debe proporcionar un **sistema de archivos**. El sistema de archivos
reside en una colección de discos; por lo tanto, la **administración del disco** debe ser
previsto

Para garantizar una ejecución ordenada, el sistema debe proporcionar mecanismos para
sincronización y comunicación, tambien puede garantizar que los trabajos no
queden atrapados en un punto muerto, esperando por siempre el uno al otro.

#### Operating-System Operations

Como se mencionó anteriormente, los sistemas operativos modernos están controlados por interrupciones
(tanto de hardware como de software).

> Si no hay procesos para ejecutar, no hay dispositivos de I/O para reparar,
> y no hay usuarios a quienes responder, un sistema operativo se sentará en silencio, esperando que suceda algo.

Dual-Mode and Multi-mode Operation
 
> Para asegurar la correcta ejecución del sistema operativo,
> debemos ser capaces de distinguir entre la ejecución de
> código del sistema operativo y código definido por el usuario

> el soporte de hardware que nos permite diferenciar entre varios modos de ejecución.

Hardware support

Como mínimo, necesitamos dos modos de funcionamiento separados: modo usuario y modo kernel (también llamado modo privilegiado).

un bit, llamado el **modo bit (mode bit)**, se agrega al hardware del computador para indicar el modo actual: kernel(0) y usuario (1)

En el momento del arranque del sistema, el hardware se inicia en modo kernel. La operacion
A continuación, se carga el sistema e inicia las aplicaciones en modo usuario.

Cuando una aplicación de usuario solicita un servicio del sistema operativo
(a través de una llamada al sistema), el sistema debe pasar del modo de usuario al modo de kernel

Algunas instrucciones designadas como privilegiadas, solo ejecutables en el modo kernel

**Transition from User to Kernel Mode**
![](/TheusZero/images/post/SistemasOperativos/11.png)

operaciones de Dual-Mode and Multi-mode

La falta de un modo dual compatible con hardware puede causar graves
deficiencias en un sistema operativo.

las **system calls** proporcionan los medios para que un programa de usuario pregunte al 
sistema operativo para realizar tareas reservadas de este, en nombre del programa usuario del programa.

Debemos asegurarnos de que el sistema operativo mantenga el control sobre la CPU

> No podemos permitir que un programa de usuario se atasque en un bucle infinito o que falle en una **system call** y que nunca le devuelva el control al sistema operativo

> Para lograr este objetivo, podemos usar un **timer** (un contador que es decrementado por el reloj físico)

Se puede configurar un **timer** para interrumpir la computadora después de un período específico

> Si el temporizador se interrumpe, el control se transfiere automáticamente al sistema operativo

## Ejercicios Importantes

## Libro

