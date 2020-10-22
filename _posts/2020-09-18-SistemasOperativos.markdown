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

Cada cosa que se ve en este post fue traducida por mi y por ende, puede tener errores, no todo esta exactamente traducido ya que 
en parte va desde mi experencia y de lo que yo entiendo para cada caso o concepto. En caso de errores fatales o importantes contactarse directame conmigo a ```robert.parra@sansano.usm.cl```.

Si existe informacion que quieras agregar, hacemela llegar de la misma manera, la leere con gusto y la colocare sin duda alguna. dicho esto, muchas gracias!

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

**clase 2**

#### Process Management

Un **proceso** es un **programa en ejecución**. Este es una unidad de trabajo dentro del
sistema. **El programa es una entidad pasiva**, **el proceso es una entidad activa**.

un proceso necesita recursos para realizar su tarea:
>> CPU, memory, I/O, files
>
>> Initialization data

Estos recursos se le entregan proceso cuando se crea o
se lo asignan a él mientras se está ejecutando.
> Cuando el proceso termina, el sistema operativo recuperará
> cualquier recurso reutilizable.

un **Single-threaded process** tiene **un contador de programa (one program counter)** 
que especifica la ubicación de la siguiente instrucción a ejecutar
> Esto quiere decir que el proceso ejecuta instrucciones secuencialmente, una a la vez, hasta que terminación

Ahora, a diferencia del anterior el **Multi-threaded process** tiene un contador de programa por cada subproceso

Normalmente, el sistema tiene muchos procesos que se ejecutan simultáneamente en una o más CPU
> esto es multiplexar el CPU entre los procesos/hilos

El sistema operativo es responsable de las siguientes actividades en la
conexión con la gestión de procesos (process management):

>> Programar procesos e hilos en las CPU
>
>> Crear y eliminar procesos de usuario y del sistema
>
>> Suspender y reanudar procesos
>
>> Proporcionar mecanismos para la sincronización de procesos.
>
>> Proporcionar mecanismos para la comunicación de procesos.

#### Memory Management

La memoria principal es un **gran array de bytes**. **Cada byte tiene su propia dirección**

La memoria principal es generalmente *el **único** dispositivo de almacenamiento grande que el
La CPU puede direccionar y acceder directamente*

> Por ejemplo, para que la CPU procese datos desde el disco, esos datos deben ser transferidos
> **primero a la memoria principal mediante llamadas de tipo I/O**.

Para ejecutar un programa, todas (o parte) de las instrucciones deben estar en la memoria.

Todos (o parte) de los datos que son necesarios para el programa deben estar en la memoria.

por eso, la **Memory management (gestión de la memoria)** determina qué hay en la memoria y cuándo esta.

Se utilizan muchos **esquemas (schemes)** de **Memory management (gestión de la memoria)** diferentes.

> Cada algoritmo requiere su propio **hardware support**

El sistema operativo es responsable de las siguientes actividades en
conexión con la **Memory management (gestión de la memoria)**

> Realizar un seguimiento de las partes de la memoria que se están siendo utilizandas actualmente y por quien la esta usando (que proceso)

> Decidir a qué procesos (o partes de los mismos) y que datos mover dentro y fuera de la memoria

> Asignar y desasignar espacio de memoria según sea necesario

#### Storage Management

Para que el sistema informático sea conveniente para los usuarios,
Este sistema proporciona una vista lógica y uniforme del almacenamiento de la información.

El sistema operativo se abstrae de las propiedades físicas de sus
dispositivos de almacenamiento para definir una unidad de almacenamiento lógica, llamada **el archivo**.

> Cada medio de almacenamiento está controlado por el dispositivo de almacenamiento (es decir, el disk drive)

> Cada medio de almacenamiento tiene sus propias características y organizacion física.
>> varias propiedad fisicas incluyen la velocidad, capacidad, data-transfer rate y el access method.

El concepto de **file (archivo)** es extremadamente general
> El sistema operativo implementa el concepto abstracto de **file(archivo)** para la
> gestión de medios de almacenamiento masivo

**File-System management (Gestión del sistema de archivos)**


los **file(archivo)** generalmente son organizados en directorios

el **Access control (Control de acceso)** se usa en la mayoría de los sistemas para determinar quién puede acceder sobre algun archivo en especifico.

#### Mass-Storage Management

Como ya hemos visto, el sistema informático debe proporcionar
almacenamiento secundario para hacer una copia de seguridad de la memoria principal.

Por lo general, los discos se utilizan para almacenar datos que no caben en la memoria principal.
o datos que deben conservarse durante un período de tiempo "prolongado"
> La gestión adecuada del almacenamiento masivo es de vital importancia

La mayoría de los programas se almacenan en un disco hasta que se cargan en la memoria.
> They then use the disk as both the source and destination of their processing

Debido a que el almacenamiento secundario se usa con frecuencia, debe usarse
eficientemente

Toda la velocidad de funcionamiento de la computadora depende del subsistema de disco
y sus algoritmos

#### Storage Hierarchy and Caching

Caching (almacenamiento en caché) consiste en almacenar partes de datos en un almacenamiento más rápido para mejorar el rendimiento
y es un principio importante de los sistemas informáticos

> Así es como funciona:
>> La información normalmente se guarda en algún sistema de almacenamiento (como memoria principal).
>
>> A medida que se usa, se copia en un sistema de almacenamiento más rápido: **el caché** esto es solo una forma temporal.
>
>> Cuando necesitamos un dato en particular, primero verificamos si está en el caché
>>> Si es así, usamos la información directamente del caché.
>>
>>> Si no es así, usamos la información de la fuente, poniendo un copiar en el caché

Las cachés solo de hardware están fuera del control del operador
sistema.

En una estructura de almacenamiento jerárquica, los mismos datos pueden aparecer 
en diferentes niveles del sistema de almacenamiento.

> La memoria principal puede verse como una caché rápida para almacenamiento secundario.

![](/TheusZero/images/post/SistemasOperativos/12.png)

#### Migration of data “A” from Disk to Register

El movimiento de información entre niveles de una jerarquía de almacenamiento.
puede ser **explícito** o **implícito**

> La transferencia de datos de la caché a la CPU y los registros suele ser una
> función de hardware, sin intervención del sistema operativo.

> La transferencia de datos del disco a la memoria suele estar 
> controlada por el sistema operativo.

En una estructura de almacenamiento jerárquica, los mismos datos pueden aparecer en
diferentes niveles del sistema de almacenamiento.

> Por ejemplo, suponga que un entero A que va a ser incrementado en 1, se encuentra en el archivo B en el disco duro

![](/TheusZero/images/post/SistemasOperativos/13.png)

![](/TheusZero/images/post/SistemasOperativos/14.png)

La operación de incremento procede emitiendo primero una operación de I/O
para copiar el bloque de disco en el que A reside en la memoria principal.
A esta operación le sigue la copia de A en la caché y finalmente en un
registro interno

En entornos **multitarea (multitasking)** (la CPU se cambia entre varios
procesos) se debe tener cuidado para asegurar que cada uno de estos
los procesos obtendrán el valor más reciente, sin importar dónde se encuentre
almacenado en la jerarquía de almacenamiento

> Así, la copia de A aparece en varios lugares

![](/TheusZero/images/post/SistemasOperativos/15.png)

En un entorno de multiprocesador, puede existir una copia de A
simultáneamente en varios cachés

> Debe proporcionar **coherencia de caché (cache coherency)** en el hardware, de modo que toda
>  la CPU tenga el valor más reciente en su caché
>  **HARDWARE issue (Problema de HARDWARE)**

#### I/O Subsystem

Uno de los propósitos del sistema operativo es ocultar 
las peculiaridades de los dispositivos de hardware para el usuario

El subsistema de I/O consta de varios componentes:
> Gestión de memoria de I/O que incluye:
>> **buffering** o almacenamiento en búfer (almacenar datos temporalmente mientras se transferido)
>
>> almacenamiento en caché (almacenar partes de datos en un almacenamiento más rápido para rendimiento), etc.

Controladores para dispositivos de hardware específicos:
> Solo el controlador del dispositivo conoce las peculiaridades del dispositivo específico al que está asignado

#### Protection and Security

**Protección**: consiste en cualquier mecanismo para **controlar el acceso de procesos o
usuarios a los recursos** definidos por el SO

> Por ejemplo, el hardware de direccionamiento de memoria asegura que un proceso se puede ejecutar solo dentro de su propio espacio de direcciones
>
> Sin embargo, un sistema puede tener la protección adecuada pero aún ser propenso a falla y permite el acceso inadecuado

Seguridad: defensa del sistema contra ataques internos y externos.

Los sistemas generalmente distinguen primero entre usuarios, para determinar quién puede
hacer qué

La mayoría de los sistemas operativos mantienen una lista de nombres de usuario y asociados
identificadores de usuario **(user IDs)**

> Estos ID numéricos son únicos, uno por usuario

ID de usuario luego es asociado con todos los archivos y procesos de ese usuario para
determinar el control de acceso

El identificador de grupo (ID de grupo) permite definir un conjunto de usuarios
controles administrados, luego también asociados con cada proceso y archivo

La escalada de privilegios permite al usuario cambiar a una identificación efectiva con más
derechos

#### Kernel Data Structures

**REVISAR EL POST DE ALGORITMOS DE ESTE MISMO BLOG: [HAS CLICK AQUI!](https://theuszer0.github.io/TheusZero/2020/07/09/Algoritmos/)**

Pasamos a continuación a un tema central para la implementación del sistema operativo: el
la forma en que se estructuran los datos en el sistema

> Describiremos brevemente varias estructuras de datos fundamentales que se utilizan ampliamente en los sistemas operativos.

**Array**:

> Un array es una estructura de datos en la que se puede acceder a cada elemento directamente. Por ejemplo, la memoria principal se construye como una matriz
>> ¿Pero qué hay de almacenar un artículo cuyo tamaño puede variar? - En tales situaciones, el array dan paso a otras estructuras de datos

Después de los arrays, las listas son las estructuras de datos más fundamentales en
Ciencias de la Computación

> se debe acceder a los elementos de una lista en un orden particular
>
> Una lista representa una colección de valores de datos como una secuencia

Las listas vinculadas se adaptan a elementos de distintos tamaños y permiten una fácil inserción
y eliminación de elementos

![](/TheusZero/images/post/SistemasOperativos/16.png)

**Stack (pila)**

>> Una pila es una estructura de datos ordenada secuencialmente que usa el último en, primero
>>  principio de salida (LIFO), lo que significa que el último elemento colocado en una pila es
>>  el primer elemento eliminado.
>
>> Las operaciones para insertar y quitar elementos de una pila son conocidas como push y pop, respectivamente
>
>> Un sistema operativo a menudo usa una pila cuando invoca una función llamadas
>
>> ![](/TheusZero/images/post/SistemasOperativos/17.png)

**Queue (cola)**

>> Una cola, es una estructura de datos ordenada secuencialmente que usa el principio de que el primero en entrar,
>> es el primero en salir (FIFO): los elementos se eliminan de una cola en el orden en
>> que fueron insertados.
>
>> Las colas son bastante comunes en los sistemas operativos
>
>> Los trabajos que se envían a una impresora normalmente se imprimen en el orden de cola
>
>> Las tareas que esperan ser ejecutadas en una CPU disponible a menudo son organizado en colas
>
>> ![](/TheusZero/images/post/SistemasOperativos/18.png)

**Arbol Binario (Binary search tree)**

Un árbol es una estructura de datos que se puede utilizar para representar
datos jerárquicamente. Los valores de datos en una estructura de árbol son
vinculados a través de relaciones entre padres e hijos

En un árbol general, un padre puede tener un número ilimitado
de niños. En un árbol binario, un padre puede tener como máximo
dos hijos, que llamamos el hijo izquierdo y el derecho
niño

>> ![](/TheusZero/images/post/SistemasOperativos/19.png)

Un árbol de búsqueda binaria también requiere un orden
entre los dos hijos

Cuando buscamos un elemento en un árbol de búsqueda binaria, el
El desempeño en el peor de los casos es O(n) (considere cómo esto puede
ocurrir).

Sin embargo, un árbol de búsqueda binario equilibrado que contiene n
elementos, tiene en la mayoría de los niveles de registro, lo que garantiza el peor de los casos
rendimiento de O (logn).

>> ![](/TheusZero/images/post/SistemasOperativos/20.png)

**Función hash (Hash function)**

Una función Hash toma datos como su entrada, realiza una operación numérica en
estos datos y devuelve un valor numérico

> Este valor numérico se puede utilizar como índice en un array para recuperar rápidamente los datos.
>> ![](/TheusZero/images/post/SistemasOperativos/21.png)

Usar una función hash para recuperar datos de la tabla puede ser tan bueno como
O (1) en el peor de los casos

Sin embargo, muchas entradas pueden dar como resultado el mismo valor de salida, es decir,
se puede vincular a la misma ubicación de la tabla

Podemos acomodar esta colisión de hash al tener una lista vinculada en esa mesa
ubicación que contiene todos los elementos con el mismo valor hash

>> ![](/TheusZero/images/post/SistemasOperativos/22.png)

>> ![](/TheusZero/images/post/SistemasOperativos/23.png)

#### Computing Environments - Virtualization

La virtualización es una tecnología que permite que los sistemas operativos se ejecuten como
aplicaciones dentro de otros sistemas operativos

La virtualización también incluye emulación

> la emulacion se usa cuando la tipo de fuente de la CPU es diferente del CPU elejido
>> ejemplo:  Allow applications compiled for the IBM CPU to run on the Intel CPU

> Sin embargo, la emulación tiene un alto precio
>> Cada instrucción a nivel de máquina que se ejecuta de forma nativa en el sistema fuente
>> debe traducirse a la función equivalente en el sistema de destino,
>> con frecuencia resulta en varias instrucciones de destino
>
>> El código emulado puede ejecutarse mucho más lento que el código nativo.
>
> Esto se conoce como interpretación (interpretation)

La interpretación es una forma de emulación en la que el lenguaje de alto nivel
se traduce a instrucciones de CPU nativas, emulando una teoría
máquina (virtual) en la que ese lenguaje podría ejecutarse de forma nativa

> Podemos ejecutar programas Java en "máquinas virtuales Java".

Un administrador de máquina virtual VMM permite al usuario instalar múltiples
sistemas operativos para exploración o para ejecutar aplicaciones escritas para
sistemas operativos distintos al host nativo

>> ![](/TheusZero/images/post/SistemasOperativos/24.png)

Las computadoras integradas son la forma más común y que mas a prevalecido

Suelen tener tareas muy específicas. Los sistemas operativos proporcionan
características limitadas -> Ellos tienen poca o ninguna interfaz de usuario

Los sistemas integrados casi siempre ejecutan sistemas operativos en tiempo real

Se utiliza un sistema en tiempo real cuando se han establecido requisitos de tiempo rígidos.
colocado en el funcionamiento de un procesador o el flujo de datos

Un sistema en tiempo real tiene limitaciones de tiempo fijas y bien definidas. El procesamiento debe realizarse dentro de las restricciones definidas, o el sistema
fallará

#### Operating System Services (Servicios del sistema operativo)

> Exploramos los tres aspectos de los sistemas operativos, mostrando los puntos de vista de usuarios, programadores y diseñadores de sistemas operativos.

Los sistemas operativos proporcionan un entorno para la ejecución de programas y
servicios a programas y usuarios

Un conjunto de servicios del sistema operativo proporciona funciones que son útiles
al usuario, como por ejemplo:

> User interface (interfaz de usuario) UI
>> Command-Line (CLI), Graphical User Interface (GUI)
>
> Ejecución de un programa: el sistema debe poder cargar un programa en
> memoria y poder ejecutar este mismo programa, ya sea normalmente o
> anormalmente (indicando el error de ejecucion)
>
> I/O operations: Un programa en ejecución puede requerir una operacion I/O, que puede
> involucrar un archivo o un dispositivo.

#### Operating System Services (Cont.) - (servicios del sistema operativo (Cont.))

Un conjunto de servicios del sistema operativo proporciona funciones que son útiles para
el usuario (Cont.):

> File-system manipulation (manipulacion de archivos del sistema): 
>> Los programas necesitan leer y escribir archivos y directorios, crear y eliminar
>>   buscarlos, listar información de archivos, gestión de permisos

> Communications (Comunicaciones)
>> Los procesos pueden intercambiar información, desde un mismo computador o entre computadoras a través de una red
>
>> 2 vías de comunicación: mediante memoria compartida o mediante mensaje pasando (a través de un buzón común)

> Error detection (deteccion de errores): El sistema operativo debe estar constantemente al tanto de posibles errores
>> Pueden ocurrir errores en la CPU y el hardware de la memoria (como un error **en memoria**
>> o un **corte de energía**), en dispositivos los dispositivos I/O 
>> (como un error de paridad en el disco, una conexión mal hecha o una
>> falla en red, etc.), y en el programa de usuario
>> (desbordamiento en memoria, o un intento de acceder a una ubicación de memoria ilegal...)
>
>> Para cada tipo de error, el sistema operativo debe tomar las medidas adecuadas para
>>  asegurar una computación correcta y consistente

Existe otro conjunto de funciones del sistema operativo para garantizar el funcionamiento eficiente de
el propio sistema a través del **resource sharing (intercambio de recursos)**

> Asignación de recursos (Resource allocation): cuando se ejecutan varios usuarios o varios trabajos
> al mismo tiempo, se deben asignar recursos a cada uno de ellos.
>> Muchos tipos de recursos: ciclos de CPU, memoria principal, archivos almacenamiento, dispositivos I/O
> 
> Contabilidad (Accounting): para realizar un seguimiento de qué usuarios usan cuánto y qué tipos de recursos
>
> Protección y seguridad (Protection and security): los dueño de la informacion almacenada en una o en multicuentas como en la red de la computadora pueden poseer el control y hacer uso de esta informacion para administrar el sistema de forma correcta, por lo que los procesos no deberian interferir entre usuarios.

**Una vista de los servicios del sistema operativo (A View of Operating System Services)**

![](/TheusZero/images/post/SistemasOperativos/25.png)

#### User Operating System Interface - CLI (Interfaz del sistema operativo del usuario: CLI)

Hay varias formas para que los usuarios interactúen con el sistema operativo.
Aquí, discutimos dos enfoques fundamentales

> Uno proporciona una interfaz de línea de comandos (CLI - (Command-LIne)) o Interprete (command interpreter)

> El otro permite a los usuarios interactuar con el sistema operativo a través de una interfaz gráfica del usuario

En sistemas con **varios comandos** para elegir, el
**intérprete** se conoce **shell** (corresponde a una CLI)

Estos comandos se pueden implementar de dos formas generales

> En un enfoque, el propio intérprete de comandos (shell-CLI) contiene el código para ejecutar el comando.

> Un enfoque alternativo implementa la mayoría de los comandos a través de programas del sistema.
> En este caso, la shell simplemente usa el comando
> para identificar un archivo que se cargará en la memoria y se ejecutará. (como el funcionamiento del PATH)

#### User Operating System Interface - GUI

Interfaz de escritorio fácil de usar

Los iconos representan archivos, programas, acciones, etc.

![](/TheusZero/images/post/SistemasOperativos/26.png)

#### System Calls (llamadas al sistema)

Las llamadas al sistema dan una interfaz de programación para los servicios que
proporciona el sistema operativo

Generalmente disponible como rutinas escritas en C y C ++, aunque
Es posible que ciertas tareas de bajo nivel deban escribirse utilizando ensamblador

Incluso los programas simples pueden hacer un uso intensivo del
sistema.

Con frecuencia, los sistemas ejecutan miles de llamadas al sistema por segundo. La mayoría de los programadores nunca ven este nivel de detalle.

**ejemplo, un programa que crea un archivo, lo lee escribe sobre este mismo. **
![](/TheusZero/images/post/SistemasOperativos/27.png)

Los desarrolladores de aplicaciones diseñan programas de acuerdo con una
interfaz de programación de aplicaciones (API)

La API especifica un conjunto de funciones que están disponibles para una aplicación.


Los tipos de llamadas al sistema se pueden agrupar aproximadamente en seis
categorías:

> process control (control de procesos)

> file manipulation (manipulación de archivos)

> device manipulation (manipulación de dispositivos)

> information maintenance (mantenimiento de la información)

> communications (comunicaciones)

> protection (protección)


Las tres API más comunes son:

> Win32 API for Windows
>
> POSIX API for POSIX-based systems (including virtually all
  versions of UNIX, Linux, and Mac OS X)
>
> Java API for the Java virtual machine (JVM)

Un programador accede a una API a través de una biblioteca de código proporcionada por
el sistema operativo

En el caso de UNIX y Linux los programas son escritos en C y la biblioteca se llama libc

**Example of Standard API**

![](/TheusZero/images/post/SistemasOperativos/28.png)

#### API – System Call – OS Relationship

![](/TheusZero/images/post/SistemasOperativos/29.png)

#### System Call Implementation (implementacion de llamadas al sistema)

Los métodos generales utilizados para pasar parámetros al sistema operativo son:
> El enfoque más simple es pasar los parámetros en registros. En algunos
> casos, puede haber más parámetros que registros
>> Entonces, los parámetros se almacenan en un bloque o tabla en la memoria y la dirección del bloque se pasa como parámetro en un registro

![](/TheusZero/images/post/SistemasOperativos/30.png)

#### Types of System Calls (tipos de llamadas al sistema)

Analizamos brevemente los tipos de llamadas al sistema que puede proporcionar un
sistema operativo

> Process control **control de procesos**
>> Un programa en ejecución puede necesitar detenerse en caso x de error, por lo que se ejecuta un **end()** o un **abort()**
>
>> Un proceso que ejecuta un programa puede querer cargar con **load()** y ejecutar con **exec()** otro programa.
>
>> Determinar y restablecer los atributos de un proceso, incluida la prioridad, su máximo tiempo de ejecución permitido, etc.
>
>> Terminar un trabajo o proceso que creamos
>
>> Esperar a que los procesos terminen su ejecución, es decir, una cierta cantidad de tiempo o un evento específico que ocurrirá
>
>> Permitir que un proceso bloquee los datos compartidos. Entonces, ningún otro proceso puede acceder al datos hasta que se libere el bloqueo. **(acquire_lock(), release_lock())** 
>
>> Asignar y liberar memoria

#### Standard C Library Example
![](/TheusZero/images/post/SistemasOperativos/31.png)

#### Example: MS-DOS

A continuación, usamos dos ejemplos: uno que involucra un sistema de una sola tarea **(single-tasking)** y
el otro, un sistema multitarea **(multitasking)**, para aclarar algunos conceptos.

![](/TheusZero/images/post/SistemasOperativos/32.png)

![](/TheusZero/images/post/SistemasOperativos/33.png)

#### Other Types of System Calls

File management
 create file, delete file
 open, close file
 read, write, reposition
 get and set file attributes

## Resumen

## Ayudantias



## Ejercicios Importantes

## Libro

