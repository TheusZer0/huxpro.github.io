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
> create file, delete file
>
> open, close file
>
> read, write, reposition
>
> get and set file attributes

 Device management
> request device, release device
>
> read, write, reposition
>
> get device attributes, set device attributes
>
> logically attach or detach devices

#### Other Types of System Calls (Cont.)

Information maintenance
> return information about the system
>
> Info for debugging
>
>> get time or date, set time or date
>
>> get system data, set system data
>
>> get and set process, file, or device attributes

#### Communication

> create, delete communication connection
>
> send, receive messages if message passing model to host name or process name
>
> Shared-memory model create and gain access to memory regions
>> Message passing is useful for exchanging smaller amounts of data
>
> attach and detach remote devices

![](/TheusZero/images/post/SistemasOperativos/34.png)

**clase 3**

El sistema proporciona un entorno conveniente para el programa
desarrollo y ejecución. Se pueden dividir en:

> Manipulacion de archivos (File manipulation)

> Estado de la informacion (Status information)

> Soporte de lenguajes de programacion (Programming language support)

> cargar programas y ejecutarlos (Program loading and execution)

> comunicacion (Communications)

> servicios ocultos para el usuario promedio (Background services)

la mayoria de las aplicaciones de los usuarios son definidas por programas del sistema, no por las actuales system calls

#### System Programs
Algunos de ellos son simplemente interfaces de usuario para llamadas al sistema; otros son
considerablemente más complejo.

Ellos se pueden dividir en estas categorías.

> File management|Status information|File modification

entre estos tambien encontramos:

> soporte para lenguajes de programacion **(Programming-language support)**:
>> Compilers, assemblers, debuggers and interpreters sometimes provided

> Carga y ejecución del programa (Program loading and execution)

> comunicacion (Communications)
>> Mechanism for creating virtual connections among processes, users, and computer systems

> Servicios de fondo (Background Services)
>> servicios que comienzan desde que se prende el sistema hasta que termina (Launch at boot time)

#### Operating System Structure

Un sistema tan grande y complejo como un sistema operativo moderno debe
ser diseñado con cuidado para que funcione correctamente y se modifique
fácilmente

> Simple Structure
>> MS-DOS es un ejemplo de tal sistema. Fue diseñado originalmente
>> e implementado para proporcionar la mayor funcionalidad en el menor espacio, por lo que no se dividió cuidadosamente en módulos
>
>> En MS-DOS, las interfaces y los niveles de funcionalidad no están bien separadas. los programas de aplicación pueden acceder a las básicas rutinas de los dispositivos I/O para escribir directamente en la pantalla y unidades de disco!

MS-DOS también estaba limitado por
hardware de su época

El Intel 8088 para el que fue
escrito no proporciona modo dual, por lo que los diseñadores no tuvieron otra opción
dejar el hardware
accesible

Asimismo, en UNIX original el
kernel proporciona el sistema de archivos,
Programación de CPU, gestión de memoria
 y otras funciones del sistema operativo a través de llamadas de sistema, 
eso es un enorme cantidad de funcionalidad a ser
combinado en un nivel.

Esta estructura monolítica fue
difícil de implementar y mantener.

![](/TheusZero/images/post/SistemasOperativos/35.png)

#### Traditional UNIX System Structure

![](/TheusZero/images/post/SistemasOperativos/36.png)

#### Modular Operating Systems

Los implementadores tienen más libertad para cambiar el funcionamiento interno del
sistema y en la creación de sistemas operativos modulares

El ocultamiento de información también es importante, porque deja a los programadores libres para
implementar las rutinas de bajo nivel como mejor les parezca, siempre que el
la interfaz de la rutina permanece sin cambios

Un sistema puede hacerse modular de muchas formas
> Un método es el enfoque por capas, en el que el sistema operativo es dividido en varias capas (niveles).
>
> La capa inferior (capa 0) es el hardware; la más alta (capa N) es la interfaz de usuario.

#### Layered Approach

Una capa M típica consta de datos y
estructuras con un conjunto de rutinas que pueden
ser invocadas por capas de nivel superior

La principal ventaja de las capas
es el enfoque en la simplicidad de construcción
y depuración

Con modularidad, se seleccionan capas
tal que cada uno use funciones
(operaciones) y servicios solo de capas de nivel inferior
> Por lo tanto, el diseño y la implementación
  del sistema se simplifican como
  cada capa esconde la existencia de
  ciertas estructuras de datos, operaciones,
  y hardware de nivel superior
  capas.

la gran dificultad con las capas es que el
enfoque involucre apropiadamente
la definicion de las distintas capas

el problema final con la implementacion
 de capas es que tienden a ser
menos eficiente que otros tipos

> Cuando un programa del usuario ejecuta una operacion I/O:
>> este ejecuta una llamada al sistema que es atrapada por la capa I/O
>> que llama ala capa del administrador de memoria, y retorna llamadas que la capa de la cpu
>> interpeta y luego son pasadas al hardware

Cada capa agrega una sobrecarga a la
llamada al sistema, es decir, que una llamada al sistema se toma más tiempo.

![](/TheusZero/images/post/SistemasOperativos/37.png)

#### Loadable Kernel Modules

> Quizás la mejor metodología actual para el diseño de sistemas operativos implica
> usar módulos de kernel cargables
>> el kernel tiene un conjunto de componentes centrales y enlaces en servicios adicionales a través de módulos

This type of design is common in modern implementations of UNIX, such as
Solaris, Linux, and Mac OS X, as well as Windows.

La idea del diseño es que el kernel proporcione servicios básicos mientras que otros
servicios se implementan dinámicamente, ya que el kernel se está ejecutando

![](/TheusZero/images/post/SistemasOperativos/38.png)

#### Procesos(processes)

Los sistemas informáticos contemporáneos permiten que múltiples programas sean
cargados en la memoria y ejecutados al mismo tiempo

> un sistema consta de una colección de procesos:
>> el sistema operativo ejecuta el código del sistema (system code).
>
>> el usuario procesa y ejecuta el codigo.

#### Process Concept

Un proceso es más que el código del programa, a veces conocido como
sección de texto ya que, Incluye la actividad actual, representada por el valor del programa como el contador y el contenido de los registros del procesador.

Un proceso generalmente también incluye la pila de procesos, que contiene
datos temporales (como parámetros de función, direcciones de retorno y
variables) y una sección de datos, que contiene variables globales.

Un proceso también puede incluir un heap, que es una memoria que es dinámicamente
asignada durante el tiempo de ejecución del proceso

Un programa se convierte en un proceso cuando se carga en
memoria

Aunque dos procesos pueden estar asociados con el mismo programa,
sin embargo, se consideran dos secuencias de ejecución independientes.

El programa es una entidad pasiva almacenada en el disco
(archivo ejecutable), el proceso es el programa cuando esta activo y cargado en memoria

La ejecucion de un programa por parte del usuario puede ser mediante el GUI

> **Un programa pueden ser varios procesos**
>> Considere la posibilidad de que varios usuarios ejecuten
   mismo programa

![](/TheusZero/images/post/SistemasOperativos/39.png)

#### Process State

Un proceso puede estar en uno de los siguientes estados:

> Nuevo: Se está creando el proceso
>
> Corriendo. Se están ejecutando instrucciones
>
> Esperando. El proceso está esperando que ocurra algún evento (como una finalización de I/O o recepción de una señal).
>
> Listo. El proceso está esperando ser asignado a un procesador.
>
> Terminado. El proceso ha finalizado su ejecución

**Diagram of Process State**

![](/TheusZero/images/post/SistemasOperativos/41.png)


#### Process Control Block (PCB)
Cada proceso está representado en el sistema operativo por un proceso
bloque de control (PCB).

**Threads - Hilos** El modelo de proceso discutido hasta ahora ha implicado que un proceso es un
programa que realiza un solo hilo de ejecución

La mayoría de los sistemas operativos modernos han ampliado el concepto de proceso a
Permitir que un proceso tenga múltiples subprocesos de ejecución y, por lo tanto,
realizar más de una tarea a la vez

> Esta característica es especialmente beneficiosa en sistemas multinúcleo, donde varios subprocesos pueden ejecutarse en paralelo

![](/TheusZero/images/post/SistemasOperativos/40.png)

#### Process Representation in Linux
Representado por la estructura C task_struct

Dentro del kernel de Linux, todos los procesos activos se representan mediante un doubly linked
list de las task struct (estructura de tareas)

![](/TheusZero/images/post/SistemasOperativos/42.png)

#### CPU Switch From Process to Process

![](/TheusZero/images/post/SistemasOperativos/43.png)

#### Process Scheduling (Programación de procesos)

El objetivo de la multiprogramación es tener algún proceso en ejecución
en todo momento, para maximizar la utilización de la CPU

El objetivo del **time sharing** tiempo compartido es cambiar la CPU entre procesos
con tanta frecuencia que los usuarios pueden interactuar con cada programa mientras se
corriendo

Para cumplir con estos objetivos, el planificador de procesos **(process scheduler)** selecciona un
proceso (posiblemente de un conjunto de varios procesos disponibles) en la memoria
para la ejecución del programa en la CPU

> **Scheduling Queues**
>> A medida que los procesos ingresan al sistema, se colocan en una cola de trabajos, que consta de todos los procesos del sistema.
>
>> Los procesos que residen en la memoria principal y están listos y esperando a ejecutarse se mantienen en una lista llamada **ready queue**
>
>> La lista de procesos que esperan un dispositivo I/O en particular se denomina cola de dispositivo. Cada dispositivo tiene su propia **device queue**

Los procesos migran entre las distintas colas

Una representación común de la programación de procesos es un diagrama de cola. **queueing diagram**

![](/TheusZero/images/post/SistemasOperativos/44.png)

#### Ready Queue And Various I/O Device Queues

![](/TheusZero/images/post/SistemasOperativos/45.png)


#### Schedulers

El sistema operativo debe seleccionar procesos de estas colas en
alguna manera. La selección la realiza el planificador correspondiente **(by the appropriate scheduler)**.

**Short-term scheduler** o **CPU scheduler** selecciona cual es el proceso debe ejecutarse a continuación y asigna CPU

**Long-term scheduler** o **(job scheduler)** selecciona cual de
los procesos deben llevarse del disco a la memoria.

En general, los procesos se pueden describir como:

> I/O-bound process: pasa más tiempo haciendo I/O que haciendo cálculos, muchas ráfagas cortas de CPU

> CPU-bound process: dedica más tiempo a hacer cálculos; few very long CPU bursts

> Es importante que el **Long-term scheduler** seleccione una buena mezcla de procesos
>> ![](/TheusZero/images/post/SistemasOperativos/46.png)

Algunos sistemas operativos, como los sistemas de tiempo compartido **(time-sharing systems)**, pueden
introducir un nivel intermedio adicional de programación. **(intermediate level of scheduling)**

La idea clave detrás de un planificador de mediano plazo **(medium-term scheduler)** es que a veces puede
Ser beneficioso eliminar un proceso de la memoria. Posteriormente, el proceso puede reintroducirse en la memoria y su ejecución
puede continuar donde lo dejó. Este esquema se llama intercambio **(swapping)**

#### Addition of Medium Term Scheduling

Se puede agregar un **Medium-term scheduler** si el grado de multiprogramación
necesita disminuir. Elimina el proceso de la memoria, almacenandolo en el disco, vuelve a traerlo del
disco para continuar la ejecución: swapping

![](/TheusZero/images/post/SistemasOperativos/47.png)

#### Context Switch

Cuando ocurre una interrupción **(interrupt)**, el sistema necesita **guardar el
contexto del proceso** que se ejecuta en la CPU para que pueda **restaurar ese
contexto** cuando se realiza su procesamiento.

> The context is represented in the PCB **(Process Control Block)** of the process.

Realizar un guardado de estado del proceso actual y una restauración de estado de un
proceso diferente, es una tarea conocida como **context switch**.

el Context-switch time es pura sobrecarga. because the system does no useful work (a typical speed is a few milliseconds)

#### Process Creation

Durante el curso de la ejecución, un proceso puede crear varios nuevos
procesos

El proceso de creación se denomina proceso padre, y el nuevo
proceso que proviene del proceso padre se denominan hijo

El proceso padre crea procesos hijos que, a su vez, crean
otros procesos, formando un árbol de procesos

Most operating systems (including UNIX, Linux, and Windows)
identify processes according to a unique process identifier (or pid),
which is typically an integer number

Cuando un proceso crea un proceso hijo, ese proceso hijo necesitará
ciertos recursos (tiempo de CPU, memoria, archivos, dispositivos de I/O)

![](/TheusZero/images/post/SistemasOperativos/48.png)

> **Resource sharing options:**
>> Parent and children share all resources
>
>> Children share subset of parent’ s resources
>
>> Parent and child share NO resources

Restringir un proceso secundario a un subconjunto de los recursos de los padres
evita que cualquier proceso sobrecargue el sistema creando demasiado
child processes

> Execution options
>> Parent and children execute concurrently
>
>> Parent waits until some or all of its children terminate

> También hay dos posibilidades de espacio de direcciones para el nuevo proceso
>> Hijo duplicado del padre (tiene el mismo programa y datos que el padre)
>
>> El niño tiene un nuevo programa cargado en él

![](/TheusZero/images/post/SistemasOperativos/49.png)

**UNIX EXAMPLE**

![](/TheusZero/images/post/SistemasOperativos/50.png)

**clase 4**

#### Process Control Block (PCB)

Información asociada a cada proceso (también llamado bloque de control de tareas **( task control block )**)

El PCB simplemente sirve como depósito de cualquier información que
puede variar de un proceso a otro

![](/TheusZero/images/post/SistemasOperativos/51.png)

#### Process Termination

Un proceso acaba cuando termina de ejecutar su declaración final
y le pide al sistema operativo que lo elimine usando la llamada al sistema **exit()**

el proceso puede devolver un valor de estado (un número entero) a su proceso padre

Un proceso puede provocar la terminación de otro proceso a través de una
llamada al sistema

Cuando un proceso crea un nuevo proceso, la identidad del nuevo se pasa al padre

El padre puede terminar la ejecución de procesos secundarios utilizando el
abort() como llamada al sistema

> El proceso hijo ha excedido los recursos asignados
>
> La tarea asignada al proceso hijo ya no es necesaria
>
> terminar con todos los procesos hijos para que el padre pueda terminar (algunos sistemas operativos tienen esa regla)

Cuando un proceso termina, sus recursos son desasignados por el
sistema operativo

![](/TheusZero/images/post/SistemasOperativos/52.png)

**Un proceso padre puede esperar la terminación de un proceso hijo
  usando la llamada al sistema wait()**
  
existe un registro que indica todos los procesos que estan acitvos en un momento dado **ps aux**

un proceso hijo que haya terminado y un proceso padre que todavia no haya terminado, se le denomina como un proceso zombie. muere pero no desaparece, es un proceso zombie (el proceso padre todavia existe porque quedo pegado en alguna parte de este estado, hasta que el proceso padre ejecute el wait)

si el padre no llama al wait y termina su ejecucion y sale del sistema, el proceso hijo puede quedarse huerfano.

**ejemplos procesos zombies**
![](/TheusZero/images/post/SistemasOperativos/53.png)

![](/TheusZero/images/post/SistemasOperativos/54.png)

Toda la memoria y los recursos asignados a un proceso se desasignan cuando
el proceso termina usando la llamada al sistema exit(). **Pero la entrada del proceso en la tabla de procesos todavía está disponible**

El proceso principal puede leer el estado de salida del proceso zombie
utilizando la llamada al sistema wait (). Después de eso, el proceso zombie se elimina de
el sistema

**clase 5**

#### Process Termination

un proceso zombi o "defunct" (difunto) es un proceso que ha completado su ejecución
pero aún tiene una entrada en la tabla de procesos, permitiendo al proceso 
que lo ha creado leer el estado de su salida. 
Metafóricamente, el proceso hijo ha muerto pero su "alma" aún no ha sido recogida.

Cuando un proceso acaba, toda su memoria y recursos asociados a él se desreferencian,
para que puedan ser usados por otros procesos.
De todas formas, la entrada del proceso en la tabla de procesos aún permanece. 
Al padre se le envía una señal SIGCHLD indicando que el proceso ha muerto; 
el manejador para esta señal será típicamente ejecutar la llamada al sistema wait, 
que lee el estado de salida y borra al zombi. 
El ID del proceso zombi y la entrada en la tabla de procesos pueden volver a usarse.

**Un proceso zombi no es lo mismo que un proceso huérfano.**
Los procesos huérfanos no se convierten en procesos zombis, sino que son **adoptados** por init (ID del proceso = 1), que espera a su hijo.

El término zombi deriva de la definición común de zombi (una persona muerta).

Los zombis pueden ser identificados en la salida por pantalla del comando de Unix ps por la presencia de una Z en la columna de estado. Los zombis pueden existir por un corto período, que típicamente significa un error en el programa padre (un bug). Igualmente, la presencia de muchos procesos zombi puede indicar problemas en el sistema, y puede acarrear una alta carga del sistema, lentitud y respuestas lentas.

#### Procesos huérfanos:

A diferencia de los zombi, los huérfanos son aquellos que se siguen ejecutando a pesar de que su proceso primario (padre) concluyo su operación. Un proceso huérfano no siempre supone un problema, pues existen circunstancias en que lo necesites y tu mismo tengas que forzar que siga corriendo.
     
Un proceso huérfano forzado se ejecuta en segundo plano sin interactuar con el de forma manual. Normalmente los generamos al iniciar un servicio que se ejecutara indefinidamente, o para que termine un trabajo que durara horas.

#### zombies process

Un proceso hijo siempre se convierte primero en un zombi antes de ser eliminado de
la mesa de proceso.

```
// A C program to demonstrate Zombie Process.
// Child becomes Zombie as parent is sleeping when child process exits.
#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>
int main()
{
    // Fork returns process id in parent process
    pid_t child_pid = fork();

    // Parent process sleeps for 50 seconds, and doesn’t call wait()
    if (child_pid > 0)
    sleep(50);

    // Child process
    else
    exit(0);
    return 0;
} 
```

#### Inter-process Communication

los procesos en el sistema pueden ser indepedientes o cooperativos

> los independientes es cuando no comparten data y no depende de data de otros procesos.
>
> los dependientes dependen de esta data de procesos externos para funcionar o realizar su trabajo

las razones para tener procesos cooperativos es la siguiente:

> compartir informacion entre procesos
>
> aceleracion de procesos con multiples cores
>
> dividir procesos con hilos
>
> convivencia entre usuarios

hay dos modelos de memoria fundamentales para la inter-comunicacion de procesos. (IPC)

> la memoria compartida
>> region de memoria que se comparte entre procesos, estos que intercambian informacion pueden leer y escribir en esta region compartida

> intercambio de mensajes
>> la comunicacion se realiza mediante el intercambio de mensajes

la memoria compartida **puede ser mas rapido que el intercambio de mensajes** el intercambio de mensajes casi siempre se implementa en el sistema usando **system calls** que pasan a travez del kernel

en memoria compartida se crea este espacio de memoria y luego se puede operar con **CRUD** dependiendo de que intencion tiene el proceso.
sin embargo, esta misma posee errores como la **incoherencia de cache**, datos que migran entre la memoria a la memoria cache.

![](/TheusZero/images/post/SistemasOperativos/55.png)

para la comunicacion entre procesos debemos establecer una region de memoria comun dentro del espacio de direccion
que el proceso esta generando.

los procesos no deben escribir simultaneamente sobre este espacio en memoria. concepto de productor y consumidor (servidor y cliente)

#### Producer-Consumer Problem

tenemos un proceso que produce informacion y otro proceso consume esta informacion

para ejecutar un productor y consumidor al mismo tiempo debemos ser capaces de crear un **shared buffer**,
que es aqui donde el productor agrega informacion y el consumidor va vaciando el buffer.

el buffer puede ser ilimitado o limitado, el consumidor puede esperar con una **queue o cola** y se puede generar un arreglo para especificar el tamano del buffer.

> Shared data

```
    #define BUFFER_SIZE 10
    typedef struct {
    . . .
    } item;
    
    item buffer[BUFFER_SIZE];
    
    int in = 0;
    
    int out = 0;
```

![](/TheusZero/images/post/SistemasOperativos/56.png)

#### Inter-Process Communication – Shared Memory

la comuniacion esta bajo el control de los procesos del usuario, no el sistema operativo. 

#### Inter-process Communication – Message Passing
el intercambio de mensajes provee un mecanismo que deja acceder a procesos para la comuniacion y la sincronizacion de acciones sin necesidad de compartir el mismo espacio de direcciones 

los mensajes a enviar pueden ser de un tamano variable o fijo

se debeen proveer almenos dos operaciones:

> send(message)
>
> receive(message)

deberia existir un enlace de comunicacion entre el proceso productor y consumidor

este enlace se puede implementar de varias maneras, entre estas se excplora la forma logica, en donde el enlace 
debe ser capaz de cumplir con las operaciones  send()/receive() de forma:
> directa o indirecta
>
> sincrona o asincronizada (Synchronous or asynchronous)

> Link Implementation issues:
>> ![](/TheusZero/images/post/SistemasOperativos/57.png)

#### Direct Communication

bajo la comunicacion directa, cada proceso necesita comunicarse debe explicitamente nombrar el proceso con 
el cual formala el link, es decir, el  send() and receive() .

> send(P, message)—Send a message to process P

> receive(Q, message)—Receive a message from process Q.

un enlace de comunicacion con estas propiedades tiene los siguientes esquemas:

> establece automaticamente entre cada par de procesos con los cuales debe comunicarse y estos procesos necesitan saber
> el identificador del otro proceso para comunicarse
>
> un enlace sera asociado entre todos procesos
>
> entre cada dos procesos debe existir al menos un enlace

este esquema excibe un tipo direccion de simetria o sincrona (symmetry)

#### Indirect Communication

en comunicacion indirecta los mensajes se envian y reciben en algo que llamamos **buzones (mailbox o ports)**

cada mailbox o port tiene una unica identificacion

un proceso puede comunicarse con otro proceso via el numero de diferentes buzones (dos procesos pueden tener diferentes buzones a los que pueden acceder) **pero tienen como condicion tener almenos un buzon en comun para asi intercambiar mensajes**

> The send() and receive()
>> send(A, message)—Send a message to mailbox A
>
>> receive(A, message)—Receive a message from mailbox A.

un solo de estos enlaces puede ser unidireccional o bidireccional y un solo enlace puede estar asociado a mas de 2 procesos.

**EXAMPLE**
>> ![](/TheusZero/images/post/SistemasOperativos/58.png)

la mailbox puede pertenecer a un proceso o al sistema operativo.

un proceso puede tener su propio buzon, si un buzon pertenece al sistema operativo debe proveer mecanismo
para hacer operaciones CRUD como minimo a este buzon.

#### Synchronization

el intercambio de mensajes puede ser bloqueantes (blocking) o no bloqueantes (non-blocking)

el bloqueantes se considera **synchronous (sincrona)**

> Blocking send - el programa que envia el mensaje se queda a la espera (se queda bloqueado) esperando que este mensaje sea recibido
>
> blockind receive - el receptor se queda bloqueado esperando que el mensaje este disponible

el **No bloqueante** es considerado **Asynchronous (Asincrona)**

> Non-blocking send - el que envia el mensaje solo enviara el mensaje y no quedara a la espera, este continuara con su code
>
> Non-blocking receive - el que receptor recibe
>> un mensaje valido
>
>> un mensaje nulo

si usamos el send() and receive() de modo bloqueante tenemos un rendezvous, ya que tendremos que el envio esperara a que su mensaje sea recibido y el receptor a que este mensaje este disponible (una cita).

#### Buffering

independiente si la comunicacion es directa o indirecta, esto sera pasado por una cola, un buffer.

> Zero capacity - La cola tiene una longitud máxima de cero; por lo tanto, el enlace no puede tener ningún mensaje esperando en él. En esto
> caso, el remitente debe bloquear hasta que el destinatario reciba el mensaje
>
> Bounded capacity - un buffer con un numero N de mensajes (buffer con capacidad limitada)
>
> Unbounded capacity - largo infinito, el envio nunca se bloquea o espera


#### Inter-Process Communication

**I/O System Call terminology**

> Que es un File Descriptor
>> el File Descriptor (descriptor de archivos), es un numero entero que identifica unicamente un archivo abierto de un proceso
>
>> un **File Descriptor table** es una coleccion de numeros enteros que son indices asignados a elementos o archivos abiertos como punteros. (para asi tener la direccion de memoria de los archivos)
>
> three standard POSIX file descriptors 
>> 0 for standard input: Read from stdin  read from fd_0 : Whenever
>> we write any character from keyboard, it read from stdin through fd_0
>
>> 1 for standard output: Write to stdout  write to fd_1 : Whenever we
>> see any output to the video screen, it’ i written to through fd_1
>
>> 2 for standard error

**Memory-Mapped Files - archivos mapeados en la memoria**: 

estos archivos requieren de llamadas al sistema y acceso al disco, nosotros podemos usar memoria virtual para rutinas de I/O

Este enfoque, conocido como **mapeo de memoria** de un archivo, permite que una parte del
espacio de direcciones virtuales quede asociada lógicamente con un archivo.

multiples procesos pueden ser alojadas o mapeadas a un solo archivo de forma concurrente, de esta forma pueden alojar su data en este archivo.

cuando este archivo se cierra, todos estos datos mapeados en el archivo se escriben en disco y se remueve la memoria virtual puesta en el proceso.

![](/TheusZero/images/post/SistemasOperativos/59.png)

#### POSIX Shared Memory
![](/TheusZero/images/post/SistemasOperativos/60.png)

**clase 06**

#### Threads

la mayoria de los programas actuales contienen multiples threads asignados **(multithreaded computer systems)**

el thread es la unidad basica que la CPU utiliza ya que estos tienen ID, se le asigan a programas y se pueden stackear.

**Motivation: ¿Why use Threads?**

![](/TheusZero/images/post/SistemasOperativos/61.png)

**Multithreaded Server Architecture**

![](/TheusZero/images/post/SistemasOperativos/62.png)

**beneficios**

> la capacidad de respuesta de la aplicacion al usar threads, ya que si este es un proceso intensivo, al iniciar la ejecucion de un algoritmo, si esto se ejecuta en un solo threads, esto consumira este thread y podra demorarse demasiado demasiado tiempo en dar una respuesta
>
> compartir recursos, los threads se comparten recursos de la ejecucion del programa
>
> es economico (mas que administrar un proceso)
>
> escalabilidad del sistema, esto es aprovechar los cores del sistema para ejecutar varios task a la vez

#### Multicore Programming

agregar varios nucleo a un solo core, el Multithreaded provee un mecanismo para un uso mas eficiente.

>> el paralelismo (mas de una tarea que se ejecuta de forma paralela)
>
>> concurrencia es mas de una tarea logra demorarse mas en el tiempo sin la necesidad de divirse la carga
> **Concurrency Vs. Parallelism**
> ![](/TheusZero/images/post/SistemasOperativos/63.png)

>> **Single & Multithreaded Processes**
> ![](/TheusZero/images/post/SistemasOperativos/64.png)

#### Amdahl’s Law

para la aproximacion o evaluacion de las ganancias de rendimiento agregando o aprovechando cores en una aplicacion.

> ![](/TheusZero/images/post/SistemasOperativos/65.png)

#### Multicore Programming

**Challenges**

> examinar las aplicaciones y encontrar cuales son las areas que se pueden dividir en un task
>
> el balance de que los threads que vamos a usar hagan un trabajo balanceado entre si, para que no colapsen
>
> lograr la reparticion de la data
>
> Testing and debugging, se hace cada vez mas dificil porque existen muchas secuencias de ejecucion que tendremos que revisar, ya que habran varios threads que deberemos revisar

**Types of Parallelism**

>> data parallelism
>
>> task parallelism

el **Data parallelism** se centra en distribuir subconjuntos de datos
a través de múltiples núcleos o cores haciendo que estos realicen la misma operación
en cada núcleo

el **Task parallelism** cada thread realiza una operacion diferente, pueden usar los mismos datos, pero seran para realizar una operacion especifica, donde cada task sera hecha solo por un thread

#### User Threads and Kernel Threads

El soporte para los threads se puede proporcionar a nivel de usuario, para threads de usuario, o por el núcleo, para los threads del núcleo.

> los threads del usuario se admiten por encima del kernel y se administran sin soporte del kernel
>
> Los threads del kernel son compatibles y gestionados directamente por el sistema operativo

#### Multithreading Models

> **Many-to-One**
> ![](/TheusZero/images/post/SistemasOperativos/66.png)
>> muchos threads de usuario que se mapean a un solo thread de kernel
>
>> el proceso sera completamente bloqueado si es que uno de esos threads hace un llamado de forma bloqueante
>
> varios subprocesos no pueden ejecutarse en paralelo en sistemas multinúcleo porque solo uno puede acceder al kernel 

> **One-to-One**
>> se puede mapear un thread de usuario a un thread de kernel
>
>> provee mas concurrencia, permitiendo que puedan hacer llamados bloqueantes y que al hacerlos, no impedir que los demas threads salgan perjudicados.
>
> ![](/TheusZero/images/post/SistemasOperativos/67.png)

> **Many-to-Many Model**
> ![](/TheusZero/images/post/SistemasOperativos/68.png)
>> es el mas flexible, tenemos varios threads de usuario que se mapean a threads de kernel 
>
>> el usuario puede crear cuantos threads necesite y estos correran en paralelo entre si
>
>> es igual que el anterior pero 2 threads pueden ejecutarse en un solo thread kernel, etc.

**examples**

![](/TheusZero/images/post/SistemasOperativos/69.png)

#### Implicit Threading

> Thread Pools
>> realizar o generar threads para atender a un cliente o a una request, toma menos tiempo crear threads para multiprocesos
>> y tambien hay que ver que los recursos no se agoten (ya que no se pueden crear threads ilimitados), para eso se utiliza el Pool Threads.
>> Se crean Threads y se dejan en un lugar, cosa que una vez que un requerimiento lo necesite, entonces este se le asigna automaticamente, tambien asi se crear
>> una cantidad maxima de threads que se pueden asigan a las tareas

> OpenMP
>> un set de API o directivas para usar soporte en la programacion paralela, nos permite identificar las regiones del programa que a nosotros nos interesa
> ejecutar de forma paralela
> ![](/TheusZero/images/post/SistemasOperativos/70.png)

**clase 07**







**clase 08**

#### semaphore

una variable entera que puede cambiar su valor con operaciones atomicas (operaciones que se ejecutan de manera ininterrumpida)
se usara el **wait() y el signal()**, siendo una la que resta y otra laque suma.
> ![](/TheusZero/images/post/SistemasOperativos/71.png)

los semaforos pueden ser binarios o pueden ser contadores, son parecidos a los mutelocks

> los semaforos pueden resolver varios problemas de sincronizacion;
> ![](/TheusZero/images/post/SistemasOperativos/72.png)

los semaforos tambien sufren de busy waiting, existe el problema de que el wait() y el signal() no pueden ejecutarse al mismo tiempo
por lo que se deben ejecutar soluciones de forma critica (como en la clase anterior), se puede modificar la definicion de las funciones para que un proceso
que ejecute el wait() se bloquee completamente esperando.

ahora los semaforos podran tener valores negativos.

**Implementation without Busy waiting (Cont.)**
> ![](/TheusZero/images/post/SistemasOperativos/73.png)

#### Deadlock & Starvation

si tenemos la implementacion de semaforos con una lista de espera, puede ocurrir una situacion en donde uno o mas procesos pueden quedar
esperando de manera infinita, ya que pueden quedar esperando a uno o mas procesos que estan en la lista de espera, por lo que si estan esperando algo
que de por si ya estaba esperando otra cosa, entonces ese caso se llama **deadlocked** (interbloqueo - ninguno avanza).

> **Deadlock & Starvation**
> ![](/TheusZero/images/post/SistemasOperativos/74.png)

> **Priority Inversion, higher priority task (H) ends up waiting for middle priority task (M) when H is sharing critical section with lower priority task (L) and L is already in critical section**

para resolver el problema de la inversion de prioridad se implementa lo que se llama un **priority inheritance protocol**, esto es la llamada
 **herencia de prioridad**, donde, si un task de prioridad High, necesita de un low, este puede heredar la prioridad del task para asi ser ejecutado por el de prioridad H

#### Classical Problems of Synchronization
problemas de sincronizacion:
> Bounded-Buffer Problem
>
> Readers and Writers Problem
>
> Dining-Philosophers Problem

#### Bounded-Buffer Problem

buffer agotado, se arregla arreglando el tamano del buffer.

>> We assume n buffers, each can hold one item
>Semaphore mutex initialized to the value 1
>
>Semaphore full initialized to the value 0
>
>Semaphore empty initialized to the value n

```
The structure of the producer process
do {
    ...
    /* produce an item in next_produced */
    ...
    wait(empty);
    wait(mutex);
    ...
    /* add next produced to the buffer */
    ...
    signal(mutex);
    signal(full);
} while (true);
```

```
The structure of the consumer process
do {
    wait(full);
    wait(mutex);
    ...
    /* remove an item from buffer to next_consumed */
    ...
    signal(mutex);
    signal(empty);
    ...
    /* consume the item in next consumed */
    ...
} while (true);
```

el escritor sera la prioridad mas alta, si un escritor es llamado, todos los demas lectores deben esperar

#### Dining-Philosophers Problem

> problema de los filosofos cenando;
>
>> ![](/TheusZero/images/post/SistemasOperativos/75.png)
> el problema es: **¿what happens if all are hungry at the same time?**

**clase 09**

#### Pthreads Synchronization

> Mutex locks
> 
> Los algoritmos de exclusión mutua (comúnmente abreviada como mutex por mutual exclusion) se usan en programación concurrente para evitar que entre más de un proceso a la vez en la sección crític
>> representan la tecnica estandar de la sicronizacion
>
>> estos se usan con mutex_t que define un mutex lock, llamamos al mutex lock con **pthread_mutex_init()**
>
>> ![](/TheusZero/images/post/SistemasOperativos/76.png)

los mutex locks and semaphores sirven para arreglar los race conditions y deadlocks

#### Transactional Memory

la memoria transactional es una secuencia de operaciones de escritura y lectura que son atomicas, si una de ellas falla, entonces
se compromete toda la transaccion, es decir, se aborta esta misma y se hace un rolled back.

tambien esta el **OpenMP** con el **#pragma omp parallel** para indicar que la region de codigo que sigue despues de eso, sera una seccion critica,
su ventaja es que es mas facil y que la creacion y administracion de los threads lo hace todo la libreria

#### Homework
![](/TheusZero/images/post/SistemasOperativos/77.png)

#### Process State

![](/TheusZero/images/post/SistemasOperativos/78.png)

#### Process Scheduling

para maximizar el uso de la CPU, este cambia la cpu de proceso a proceso de forma muy rapida, este tiene que elejir entre colas de procesos

![](/TheusZero/images/post/SistemasOperativos/79.png)

#### Schedulers

**Short-term scheduler (or CPU scheduler)** selecciona cual sera el proceso que sera ejecutado 
siguiente y alojado por la cpu

**Long-term scheduler (or job scheduler)** lo que hace es selccionar cual sera el proceso que debe traer del disco duro
a la memoria y dentro de la lista ready. **controla la cantidad de procesos que se encuntran al mismo tiempo en la memoria del sistema - controls the degree of multiprogramming**

![](/TheusZero/images/post/SistemasOperativos/80.png)

#### Basic Concepts

Maximum CPU utilization: el objetivo del multiprogramming es tener varios procesos corriendo al mismo tiempo

![](/TheusZero/images/post/SistemasOperativos/81.png)
![](/TheusZero/images/post/SistemasOperativos/82.png)

#### CPU Scheduler

![](/TheusZero/images/post/SistemasOperativos/83.png)

#### Dispatcher

el despachador es un modulo que le da control a la CPU para seleccionar procesos que seran envueltos en las acciones del CPU Scheduler

> switching context
>
> switching to user mode
>
> umping to the proper location in the user program to restart that program

#### Scheduling Criteria

> CPU utilization - mantener la cpu lo mas ocupada posible
>
> Throughput: cantidad de trabajo divida del tiempo total
>
> waiting time: tiempo de espera que el proceso estaba en la cola sin ejecutarse
>
> Turnaround time: tiempo del proceso desde que entro a la cola, hasta que termino completamente de ejectarse
>
> Response time: tiempo que toma el proceso para dar una primera respuesta

#### Scheduling Algorithm Optimization Criteria

los algoritmos tratan de maximizar lo siguiente:

> Max CPU utilization
>
> Max throughput
>
> Min turnaround time
>
> Min waiting time
>
> Min response time

#### First- Come, First-Served (FCFS) Scheduling

es el mas simple algoritmo para la CPU-scheduling, es atender por orden de llegada, usa una fila FIFO.
A pesar de ser simple, su desventaja es que el tiempo de espera la mayoria de las veces es largo.

![](/TheusZero/images/post/SistemasOperativos/84.png)

> Suppose that the processes arrive in the order:
>> ![](/TheusZero/images/post/SistemasOperativos/85.png)

>> Convoy effect - short process behind long process
> CPU-bound process: se demora mucho
>
> I/O-bound processes: se demora poco

#### Shortest-Job-First (SJF) Scheduling

nos fijamos en el largo del proximo CPU burst, para dar prioridad a los I/O que demoraran menos tiempo en ejecutarse

SJF es óptimo: proporciona un tiempo de espera promedio mínimo para un
conjunto dado de procesos

>> **EXAMPLE**
> ![](/TheusZero/images/post/SistemasOperativos/86.png)
>
> ![](/TheusZero/images/post/SistemasOperativos/87.png)

#### Priority Scheduling

El SJF es un algoritmo que funciona a base de prioridades, la prioridad seria un numero entero
que seria asociado a algun proceso que indica si es mayor o menor prioridad sobre otros procesos.

Mientras menor sea el numero, mayor sera la prioridad ya que sera mas rapido de ejecutar, si hay 2 que tienen la misma prioridad, los atendemos por orden de llegada.

![](/TheusZero/images/post/SistemasOperativos/88.png)

#### Round Robin (RR)

![](/TheusZero/images/post/SistemasOperativos/89.png)

**clase 10**

#### Multilevel Queue Scheduling

es otra clase de scheduling algorithms que son creados para clasificar de manera facil y rapida
los diferentes grupos de procesos.

> multilevel queue scheduling : este algoritmo divide la ready queue en varias colas separadas, por ejemplo; una cola para el background y otro para procesos activos.
>> cada cola tiene su propio scheduling algorithm:
>>
>> foreground – RR | background – FCFS

#### Multilevel Queue

asignar un Time slice para asignar un porcentaje para hacer mas justo cual tendra mas prioridad. el foreground o el background

#### Multilevel Feedback Queue Scheduling

Normalmente, cuando se utiliza el algoritmo de multilevel queue,
los procesos se asignan permanentemente a una cola y no se mueven
de una cola a otra.
Esta configuración tiene la ventaja de una baja sobrecarga (overhead) de programación, pero es
no es flexible.

Ahora en diferencia, si se usa el algoritmo **multilevel feedback queue** este nos dejara
mover procesos de una cola a otra (a diferencia del anterior), de esta manera, la idea sera separar
los procesos que usan CPU burst

Si el proceso usa mucho tiempo la CPU sera movido a una cola de prioridad baja, a su vez, si un proceso usa poco CPU sera movido a una cola de prioridad alta. De esta forma se previene la **aging prevents starvation.** 

parametros que se deben seguir para una cumplir con una buena multilevel feedback queue scheduler:

> number of queues
>
> scheduling algorithms for each queue
>
> method used to determine when to upgrade a process to a higher priority queue
>
> method used to determine when to demote a process to a lower priority queue
>
> method used to determine which queue a process will enter when that process needs service

![](/TheusZero/images/post/SistemasOperativos/90.png)

**certamen 2**

> **clase 12**

memoria es un arreglo unidimensional donde cada segmento de memoria es un byte y lo unico que ve es un stream (cada
direccion de memoria tiene una orden especifica, sin embargo, el sistema no dicierne entre estas)

> Main Memory - RAM | Registers (registros de datos guardados en la CPU) - CPU

solo esos 2 lugares, RAM Y CPU son donde la CPU puede acceder inmediatamente (directamente, tiempo de respuesta nulo).

registros en la cpu toman un solo ciclo en accederse, lo que no esta en este, toma mucho mas tiempo, ademas se debe 
proteger el proceso de un usuario de los demas, esa proteccion debe proveerla el hardware.
para separar el espacio de memoria entre procesos se utiliza el registro base y el registro limite.

el registro base tiene el inicio del espacio de direcciones que corresponde a un proceso, el limite tiene todo el rango es decir
LA BASE + EL ESPACIO ASIGNADO O LIMITE PARA EL PROCESO.

>> BASE = 300040 | LIMIT = 120900
> TOTAL= BASE+LIMIT -> 420940
> ![](/TheusZero/images/post/SistemasOperativos/91.png)
> Todo se realiza en kernel mode
>> ![](/TheusZero/images/post/SistemasOperativos/92.png)

usualmente un programa reside en el disco duro en un archivo binary ejecutable, sin embargo para ser ejecutado debe cargarse
en memoria. todos los procesos que estan esperando a ser cargados en memoria para su ejecucion se le llama **input queue**.

> un programa pasa entre diferentes steps antes de su ejecucion:
>> las direcciones del programa generalmente son simbolicas, un compilador hace un binding (correspondencia)
>> y con eso las convierte en direcciones **relocatable** o bien, direcciones que tienen un punto de referencia en la memoria
>
>> luego el linkage editor convierte las direeciones bindeadas en direeciones reales

> Address binding of instruccions and data to memory addresses
>> **Compile time**: si todas las direcciones absolutas se generan al momento de compilar, entonces sabriamos en la localizacion de memoria
>> pero si por alguna razon este proceso debe moverse, tendriamos entonces que recompilar el programa.
>> El programa será asignado a un lugar específico y conocido de la memoria física. La direcciones de memoria son referenciadas en forma absoluta (static relocation).
>
>> **Load Time**: solo generara codigo relocatable si la localizacion de memoria no se conoce al momento de compilar el programa
>
>> **Execution time**: el binding se retrazara solo si al momento de correr el programa el proceso puede moverse durante
> su ejecucion de un segmento de memoria a otro (se necesita soporte de hardware).
> ![](/TheusZero/images/post/SistemasOperativos/93.png)

las direcciones de memoria generadas por la CPU se conocen como **logical addres**

las direcciones que llegan al controlador de memoria para solicitar acceso a la memoria son **physical address**

> Se definen varios tipos de direccionamiento:
>> Direccionamiento físico (physical address): La unidad de memoria manipula direcciones físicas.
>
>> Direccionamiento virtual (virtual address): Son las direcciones lógicas que se generan cuando existe
>> asociación de direccionamiento en tiempo de ejecución.

el compile time y el load time generan **logical addres** y **physical address** identicas, sin embargo, en el 
execution time su address-binding debe ser con solo una direccion, es decir, que no puede tomar physical address y logical addres
al mismo tiempo, estas difieren.

Memory Management Unit (MMU) se encarga de la traducción de las direcciones lógicas (o virtuales) a direcciones físicas (o reales), la protección de la memoria, el control de caché.

La traducciones de direcciones lógicas a físicas son
hechas por la MMU (Memory Management Unit)

Los procesos solo manipulan direcciones lógicas y no
visualizan las físicas, que solamente son vistas por la
MMU.

ahora el registro base sera llamado **relocation register** y este valor se agrega a cada una de las direcciones logicas que se generan a processos del usuario.

el user program nunca ve las direcciones physical reales, son direcciones virtuales.

![](/TheusZero/images/post/SistemasOperativos/95.png)

#### dynamic loading

las rutinas que no
son utilizadas, no son cargadas en memoria física y, por
lo tanto, no consumen recursos innecesariamente

el dinamyc loading se ua para una mejor utilizacion del espacio en memoria, este consiste en que algunas rutinas no se cargaran si no son llamadas, (cuando sean llamadas se cargaran).

#### dynamic linking

Ensamblador (linker): combina todos los archivos objetos
de un programa dentro de un único archivo objeto

En la etapa de ensamblaje de un programa las bibliotecas
compartidas pueden incorporarse al archivo ejecutable
generado (ensamblaje estático o static linking)

Otra alternativa es que las bibliotecas compartidas sean
cargadas en tiempo de ejecución (ensamblaje dinámico o
dynamic linking). todos los programas estan haciendo referencia a la misma libreria.

En los archivos ejecutables las bibliotecas estáticas son
incorporadas, mientras que para las dinámicas se
mantiene una referencia.

Esto permite, junto con la carga dinámica, hacer un uso
más eficiente de la memoria, ya que las bibliotecas
dinámicas se cargan una única vez en memoria principal

#### swapping

CPU <--(CONTEND SWITCH)--> MEMORY <--(SWAPPING)-->DISK

un proceso debe llegar a la memoria principal para ser ejecutado. en la memoria aveces 
no habra espacio y por eso deberemos
sacar un proceso que este cargado en memoria para ser intercambiado por el que si debe ser cargado en memoria.
aquellos que salen de memoria seran almacenados en el disco duro (swapping continuo), mover processos entre la memoria
principal y el disco duro (backing store).

> el CPU scheduler decide ejecutar un proceso recibe el nombre de dispatcher.
>> este chequea si el proceso que sera cargado en memoria tiene espacio disponible en la memoria principal
>>
>> si este no tiene espacio en la memoria principal, entonces el **distpatcher realiza un swap con algun proceso**
>> que se encuentra cargado en memoria.
> ![](/TheusZero/images/post/SistemasOperativos/96.png)

no debemos hacer un swapping a procesos que esten hacinedo I\O, ya que estos estan escribiendo datos.
una de las soluciones es que, la ejecucion de operaciones I\O sea escrita en un buffer y que este sea luego
escrito en memoria.

los sistemas operativos actuales no usan el standard swapping.

#### Context Switch Time including Swapping
contend switch
![](/TheusZero/images/post/SistemasOperativos/149.png)


#### contiguous memory allocation

> asignacion de memoria de forma contigua, la memoria se divide en dos particiones
>> procesos del sistema operativo | procesos del usuario
> estos se organizan de forma contigua

para proteccion de memoria se usan el relocation register y el limit register.
![](/TheusZero/images/post/SistemasOperativos/97.png)

#### multiple-partition allocation

dividir la memoria en particiones de tamano fijo, asi el grado de multiprogramming se limita a la cantidad de particiones
que fueron creadas.

cuando una particion esta libre, se selecciona un proceso de la input queue y es cargado dentro de la particion libre.

cuando un proceso sera ejecutado en la memoria principal, se buscara un segmento (hole) lo suficientemente grande para albergar al proceso.

![](/TheusZero/images/post/SistemasOperativos/98.png)

En la asignación de memoria a un proceso existen varias
estrategias:
> First fit: Asigna el primer “agujero” de memoria libre que satisface la necesidad, da igual si es muy grande o muy justo
> es el mas rapido pero un proceso que necesita poco hole puede usar uno extremadamente grande. 
>
> Best fit: Asigna el mejor “agujero” de memoria libre que
exista en la memoria principal (un poco mas lento, pero es el mejor)
>
> Worst fit: Asigna el requerimiento en el “agujero” más
grande que exista en la memoria principal.

#### external fragmentation
![](/TheusZero/images/post/SistemasOperativos/99.png)

![](/TheusZero/images/post/SistemasOperativos/100.png)

#### Internal Fragmentation
![](/TheusZero/images/post/SistemasOperativos/101.png)

> solucion para la fragmentacion externa:
>> ![](/TheusZero/images/post/SistemasOperativos/102.png)
> mover todos los procesos al final de la memoria para asi compactar cada uno de estos agujeros libres en un solo segmento.

#### segmentation
![](/TheusZero/images/post/SistemasOperativos/103.png)

![](/TheusZero/images/post/SistemasOperativos/104.png)

**clase 13**

Es una manera de relocalizacion dinamica

El espacio de direcciones fısicas esta dividido en zonas de tamano fijo llamadas frames de pagina

El espacio de direcciones logico o virtual esta formado por zonas de tamano fijo denominadas paginas

La direccion logica se compone de numero de pagina y desplazamiento dentro de la pagina

Con el numero de pagina se obtiene una entrada en una tabla de paginas, en donde hay una direccion base de marco de pagina

La direccion de memoria fısica a la que se accede se obtiene sumando
el desplazamiento a la direccion base del marco de pagina

Se necesita soporte del hardware (el uso del paging es similar a la tabla de base o relocation).

![](/TheusZero/images/post/SistemasOperativos/105.png)

Con paginacion la memoria de un proceso no es contigua

> La paginacion no tiene fragmentacion externa, pero sı interna.
>> A mayor tamano de pagina mayor fragmentacion interna
>
>> A menor tamano de pagina mayor gasto adicional en, p.e., tablas de paginas
>  ![](/TheusZero/images/post/SistemasOperativos/108.png)

![](/TheusZero/images/post/SistemasOperativos/106.png)

![](/TheusZero/images/post/SistemasOperativos/107.png)

el sistema operativo mantiene una copia de la page table de cada proceso

el page table se mantiene en la memoria principal

el PTBR Page-Table base register -> apunta a la tabla de paginas

el PTLR Page-Table length register -> indica el tamano de la tabla de paginas

![](/TheusZero/images/post/SistemasOperativos/109.png)

existe un problema, ya que acceder a la page table requiere de por si un ciclo a la memoria principal ya que es ahi
donde esta se almacena, por lo que en si, necesitariamos 2 ciclos, uno para ir a la memoria principal y otro para acceder
al byte. La solucion para este problema es crear un cache llamado TLB (translation look-aside buffer).

El TLB es una memoria asociativa, de rapida velocidad.
El TLB consiste en dos partes, uno es el tag y otro es el value.
La busqueda en memorias asocitavias es muy tapida, forma parte de la instruccion del pipeline.

cuando una direccion logica es generada por la CPU, el page number esta presente en el TLB.
Si el Page Number es encontrado, el marco (frame number) sera inmediatamente usado para acceder a memoria.
En el caso de que NO este en el TLB (TLB MISS) la referencia a memoria debe hacerse en la page table hacerse.

![](/TheusZero/images/post/SistemasOperativos/110.png)

![](/TheusZero/images/post/SistemasOperativos/111.png)

#### tiempo de acceso efectivo
![](/TheusZero/images/post/SistemasOperativos/113.png)

![](/TheusZero/images/post/SistemasOperativos/112.png)

#### memory protection
hay bits de proteccion asociados a cada frame de la page table.

![](/TheusZero/images/post/SistemasOperativos/114.png)

![](/TheusZero/images/post/SistemasOperativos/115.png)

![](/TheusZero/images/post/SistemasOperativos/118.png)

![](/TheusZero/images/post/SistemasOperativos/116.png)

#### hashed pages tables
![](/TheusZero/images/post/SistemasOperativos/117.png)

**clase 14**

#### virtual memory that is larger than physical memory

![](/TheusZero/images/post/SistemasOperativos/120.png)

![](/TheusZero/images/post/SistemasOperativos/119.png)

#### demand paging

cargar las paginas solamente cuando estas son necesarias, es similar al paging de las clases anteriores pero con swapping.

se aplica el esquema del invalid o valid bit para distingir entre que paginas estas en memoria o en el disco. Si una pagina
es Valida entonces es legal y esta en memoria. Si es invalida, entonces esta o no es legal o no se encuentra en memoria y
 debe ser cargada desde el disco duro.

#### valid-invalid bit
![](/TheusZero/images/post/SistemasOperativos/121.png)

> **page table when some pages are not in main memory**
> ![](/TheusZero/images/post/SistemasOperativos/122.png)

#### page fault

page fault -> page marcada como invalido

> pasos:
>> el hardware de paging causa un trap
> 
>> se busca el free frame en el disco duro
>
>> una vez encontrado se hace el swap desde el disco al page table
> 
>> se actualiza la tabla y la page table ahora tiene el V de valido
>
>> se reincia la instruccion que causo el page fault
> ![](/TheusZero/images/post/SistemasOperativos/123.png)

#### instruccion restart

> ![](/TheusZero/images/post/SistemasOperativos/124.png)

si hay un page fault al momento de copiar o reescribir datos habra un gran problmea, ya que si esto ocurre a la mitad
habria informacion que ya fue escrita.

una solucion es comprobar primero si todas las pages estan validas para que no ocurra un page fault, o bien, hacer un
buffer para la informacion.

#### performance of demand paging

> ![](/TheusZero/images/post/SistemasOperativos/125.png)

> ![](/TheusZero/images/post/SistemasOperativos/126.png)

#### copy and write 

ejemplo fork():
> ![](/TheusZero/images/post/SistemasOperativos/127.png)

#### page replacement

imagina el caso donde el usuario esta ejecutando un proceso y ocurre un page fault.
ahora este saca un frame del disco y cuando va a actualizarlo en la page table se da cuenta
de que todos estan ocupados y no hay ninguno libre. 

> Unas de las soluciones pueden ser:
>> terminar el proceso: no deberia ocurrir nunca
>
>> hacer un swap de algun proceso
>
>> reemplazo de algunas paginas (encontrar un frame que no este siendo utilizado y se
>>  reemplaza por el que debe utilizarce)

cuando esto ocurrre son 2 ciclos que se hacen. mover el page del disco y reemplazar el frame.

para reducir este overhead se usa un modify bit (bit sucio o dirty bit).

> ![](/TheusZero/images/post/SistemasOperativos/128.png)
> ![](/TheusZero/images/post/SistemasOperativos/129.png)

**clase 15**

virtual memory -> la ejecucion de los procesos que no estan completamente en la memoria, asi de esta forma los programas pueden ser mucho mas grandes.

#### page and frame replacement algorithms

![](/TheusZero/images/post/SistemasOperativos/130.png)

#### first-in first-out FIFO algorithm

![](/TheusZero/images/post/SistemasOperativos/131.png)

su rendimiento no es tan bueno, ya que solo mira el historia segun el orden FIFO, por lo que al hacer una eleccion puede a la larga tomar mas tiempo que otros algoritmos.

> belady's anomaly
> ![](/TheusZero/images/post/SistemasOperativos/132.png)

#### Optimal Page Replacement Algorithm

resuelve la anomalia anteriormente descrita.

este algoritmo necesita mirar hacia el futuro (que es imposible), por lo que
solo se considera teoricamente para benchmarks o cosas asi.

> se reemplaza la pagina que no sera usada por el periodo mas largo de tiempo:
> ![](/TheusZero/images/post/SistemasOperativos/133.png)

#### LRU - LEAST RECENTLY USED ALGORITHM
![](/TheusZero/images/post/SistemasOperativos/134.png)

tambien se le implementa un stack para que de esta manera el algoritmo sea
aun mas eficiente ya que asi podremos ver de manera correcta el uso de LRU, esto es de la siguiente forma:

![](/TheusZero/images/post/SistemasOperativos/135.png)

con esto sabemos cual es la pagina mas lejos y las mas reciente, desde abajo hacia arriba (abajo no usada recientemente).

el LRU no tiene la BELADY ANOMALY.

#### fixed allocation

la manera mas simple de dividir M frames en N procesos en darle a cada proceso la misma
cantidad de frames que a sus iguales, es decir:
![](/TheusZero/images/post/SistemasOperativos/136.png)

sin embargo los procesos pueden no ocupar todos los frames asignados, por ello
lo mejor es optar por la **PROPORTIONAL ALLOCATION**
![](/TheusZero/images/post/SistemasOperativos/137.png)

#### Global vs local allocation

**global replacement**: un proceso selecciona el frame que va a reemplazar segun
todos los frames del set de frames del sistema, esto es usado a procesos de high-priority.
un proceso no puede controlar el page-fault rate de si mismo, y esto afecatra su ejecucion y la ejecucion de procesos
de baja prioridad.

**local replacement**: cada proceso tiene su asignacion y no le quita 

**clase 16**

#### trashing

la alta actividad de paging se llama trashing, un proceso esta en trashing si se mantiene ocupado solamente haciendo swapping
de paginas de disco a la memoria o al revez, en vez de ejecutarse.

> que provoca el trashing
> 
>> cuando el sistema se entera de una baja utilizacion de la cpu, para incremetar el uso (traer mas procesos para usar toda la cpu)
>> se utiliza un algoritmo de reemplazo de paginas, sacrificando frames.
>
>> generan pagefault y obtienen frames de otros procesos (quitan espacios de procesos, entonces cuando estos se ejecutan generan pagefault tambien y caga todo)

> para lidiar con esto se debe:
>> con un algoritmo de reemplazo local puede solucionarse el problema, es decir, que se reemplazara dependiendo de la prioridad del proceso

#### working set-model

![](/TheusZero/images/post/SistemasOperativos/138.png)

#### page-fault frequency
el trashing es una alta frecuencia de generacion de pagefault entonces, si queremos controlar el trashing, no necesitamos monitorear el
working set de cada uno de los procesos, con mirar el **page fault frequency** bastaria.

![](/TheusZero/images/post/SistemasOperativos/139.png)

![](/TheusZero/images/post/SistemasOperativos/140.png)

el trashing y el resultante de swapping tiene un gran impacto sobre el rendimiento de un sistema

**clase 17**

#### overview of mass storage structure

> RPM: common drivers spin (5400, 7,200, 10000, 15000) rotations per minute

![](/TheusZero/images/post/SistemasOperativos/141.png)

disk speed has two parts:

> ritmo de transferencia, es el ritmo segun los datos se mueven entre el disco duro y el cputador (bus de datos)
>
> tiempo de posicionamiento o random-acces time
>> seek time: tiempo necesario para mover el brazo que lleva todos los cabezales
>
>> rotational latency: tiempo exacto para que el cabezal llegue al track especifico que estamos buscando

bus de entrada y salida I/O bus es para la comunicacion eentre el disco y la PC

>  controladores:
>> host controller
>> disk controller
> cada uno se comunica con el otro para relacionar datos y leer y enviar datos a la memoria

#### hard disk performance
![](/TheusZero/images/post/SistemasOperativos/142.png)

#### disk structure
![](/TheusZero/images/post/SistemasOperativos/143.png)

#### Disk Scheduling

existen algoritmos que sirven para programar la atencion de los requerimientos de I/O del disco

![](/TheusZero/images/post/SistemasOperativos/145.png)


#### FCFS
![](/TheusZero/images/post/SistemasOperativos/144.png)

#### SSTF

shortest-seek-time-fisrt, atiende primero a los mas cercanos al primer cabezal o requerimiento.

![](/TheusZero/images/post/SistemasOperativos/146.png)

pero podriamos tener casos de starvation, a pesar de mejorar muchisimo no es el optimo por eso mismo, por el caso de starvation.

#### SCAN

escanea de izquierda a derecha (y atiende todos los requerimientos). 

![](/TheusZero/images/post/SistemasOperativos/147.png)

#### CIRCULAR SCAN

![](/TheusZero/images/post/SistemasOperativos/148.png)



## Ayudantias

![](/TheusZero/images/post/SistemasOperativos/Ayudantias/1.png)

![](/TheusZero/images/post/SistemasOperativos/Ayudantias/2.png)

#### Certamen 2

>> Contiguos allocation, asignacion contigua
> 
>> como el archivo ocupaba 5 bloques y ahora se extendio 3 mas, entonces ahora ocupa 8 bloques, como empieza en el 21, el 22 que es el que le sigue tiene de espacio 2 (LEN), por lo que este debera buscar un nloque con espacio mayor o igual a 8 bloques, siguiendo la estrucutra de listas simplemente enlazada
> ![](/TheusZero/images/post/SistemasOperativos/Ayudantias/3.png)

>> Indexed Allocation , memoria indexada
> 
>> memoria indexada de niveles, tamano maximo de archivo, espacio total del disco, BIT VECTOR (bit vector), administrar espacio libre.
> ![](/TheusZero/images/post/SistemasOperativos/Ayudantias/4.png)
> 1: ![](/TheusZero/images/post/SistemasOperativos/Ayudantias/5.png)
> 2: ![](/TheusZero/images/post/SistemasOperativos/Ayudantias/6.png)

>> Free-Space List
> 
> ![](/TheusZero/images/post/SistemasOperativos/Ayudantias/3.png)

## Libro

## Resumen

## Ejercicios Importantes


