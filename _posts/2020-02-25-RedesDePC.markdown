---
layout: post
title: "Redes de Computadoras - 2019-2 "
subtitle: 'Ramo Redes de Computadoras - 2do Semestre 2019'
date: 2020-02-25 12:00:00
author: "TheusZero"
header-img: "images/post/redes.png"
catalog: true
comments: true
tags:
  - Programacion
  - USM
  - Java
  - Tareas
  - Redes
---

# Redes de Computadoras - 2do Semestre 2019 - Rudy Malonnek

## Drive

Este es un drive con mucho material para que puedan revisar y/o estudiar, pueden agregar cosas ya que mientras mas material, mejor.
   
> [Drive hecho por mi UwU](https://drive.google.com/drive/u/0/folders/0AP6afRafbeuIUk9PVA)
>> Pedira acceso, casi siempre lo acepto el mismo dia. Cualquier consulta pueden hacermelo llegar por interno.


## Links ricolinos

#### Codigos AES
> [Codigo-Java-AES](https://fluidattacks.com/web/defends/java/cifrar-simetricamente/)

#### Codigos RSA
> [Codigo-Rsa](https://www.devglan.com/java8/rsa-encryption-decryption-java)

> [Codigo-Rsa](https://mkyong.com/java/java-asymmetric-cryptography-example/)

## Consejos

Redes de computadoras es un ramo completamente de materia, conceptual y de estudio.
Creo que es solo leer y estudiar (como cualquier otro ramo) sin embargo creo que igual depende de quien te toque como profesor, por eso dare los siguientes consejos en base a mi experencia y la obtenida por los cabros de TC:

#### Rudy

Rudy es un profe que te preguntara cosas que te pase en clases (eso es bueno), te preguntara cosas super especificas, como un codigo java o un comando en linux utilizado en clases asi que:
>> aprenderse los java de memoria
>
>> Anotar todos los comandos linux que use y para que sirven
>
>> Estudiar de las PPT

#### AGV

Creo que AGV es un profe cabron ya que pregunta cosas que no pasa, sin embargo creo que como dicta el ramo es movido, tiene tareas y proyectos divertidos y no tan complejos, por lo que puedes ganar notas de buena manera.

El problema son sus certamenes, muchas veces webeados y con materia super especifica que no siempre se encuentra en las PPT por eso mis recomendaciones son:

>> Estudiar del libro, no tanto de las PPT
>
>> Estudiar de certamenes anteriores, que se encuentran en su pag (Pag hecha a puro html sdkjfghsdjfhskd, pongale css o alguna wea para que se vea linda profe:c)
>
>> Revisar Tareas anteriores (casi todas son iguales)   

AGV tiene una pag [This!](http://profesores.elo.utfsm.cl/~agv/elo322/1s19/index.html), donde cambiando la url (en la parte de **1s19** por el semestre-año que gustes) puedes acceder al semestre que dicto con sus respectivos certamenes y tareas.

Suerteeee uwu.

## Tarea 1:

#### Introduccion

El protocolo HTTP es una sigla que significa Hyper Text Transfer 
Protocol, o Protocolo de Transferencia de Hipertexto, que propone ser 
un protocolo sencillo entre cliente-servidor que articula cambios de 
información entre los clientes y los servidores HTTP. 
El principal objetivo de éste informe será interiorizar a los estudiantes 
a éste protocolo de manera práctica. 
Con la aplicación Wireshark y un servidor web se deberán analizar 
dos URL que son: 

> http://ramos.elo.utfsm.cl/~elo322/index1.html 
> http://ramos.elo.utfsm.cl/~elo322/index2.html 

El propósito es usar Wireshark como herramienta para lograr 
identificar los protocolos que se utilizan, la versión de protocolo que 
se emplea, obtener datos como el IP y los puertos utilizados, lograr 
deducir cómo funciona el envío de parámetros ingresados en cada una 
de las paginas que se nos entregan, además de poder encontrar datos 
como los bytes transferidos, estimar el tiempo que se utilizo en el 
envío de paquetes y encontrar el número de conexiones utilizadas. 

#### Desarrollo

El siguiente desarrollo se realizará mediante una máquina virtual 
Linux (Kali-Linux), en este caso Wireshark venía previamente 
instalado en el dispositivo. Si por algún motivo, este no viniera 
previamente instalado en Linux-Debian se utiliza el siguiente 
comando para instalarlo, ya que se usa el administrador de paquetes 
“APT” que Debian posee: 

> sudo apt-get install Wireshark 

Luego se accede al terminal de la máquina, utilizando los comandos 
“ifconfig” y “netstat -i”, con lo que se puede visualizar la IP de la 
máquina y las respectivas configuraciones que posee, en donde se 
determina que el interfaz de red que se usará corresponde a “eth0”.

![](/TheusZero/images/post/Redes/redes1.png)

Una vez conocida la IP de la máquina que se está utilizando, 
“192.168.236.128”, proseguimos con Wireshark:

![](/TheusZero/images/post/Redes/redes2.png)

Se utilizará la opción “Capture” que se encuentra en la barra de 
herramientas, donde luego se comienza a escanear el tráfico de red, 
es decir, comienzan a capturarse los paquetes, sólo para la interfaz de 
“eth0”. 

En el navegador, accedemos al URL: 
> http://ramos.elo.utfsm.cl/~elo322/index1.html 

donde se completan los datos requeridos y luego se recibe la respuesta por parte del servidor. 

![](/TheusZero/images/post/Redes/redes3.png)

![](/TheusZero/images/post/Redes/redes4.png)

Al recibir la respuesta, se puede notar que la respuesta que entrega el 
servidor envía a una URL distinta a la que se ingresa en primer lugar, 
lo que identifica que el método empleado para la web es GET (envía 
los datos usando la URL). 

Al revisar Wireshark, se filtraron los paquetes para revisar la 
respuesta entregada por el servidor. 

Con el filtro 
> “tcp.srcport==80 || udp.srcport==80” 

se logra obtener todos los paquetes que utilizaron la conexión de tipo TCP (Transmission Control Protocol) y UDP (User Datagram Protocol) para el puerto 80. 

![](/TheusZero/images/post/Redes/redes5.png)

Con el filtro se logra visualizar que el protocolo que se está utilizando 
es HTTP, por lo que se procede a filtrar nuevamente los paquetes, 
pero ahora sólo con el protocolo reconocido, es decir, HTTP. 
Con el filtro utilizado, los paquetes se reducen a un total de 4, los que 
serán estudiados bajo el protocolo HTTP y con destino al IP del 
Servidor. 

![](/TheusZero/images/post/Redes/redes6.png)

Analizando los paquetes con Wireshark, se selecciona el paquete de 
respuesta que envía el servidor y luego sobre el se emplea la opción 
“Follow” seguida por la opción “HTTP stream” para poder revisar los 
detalles de las peticiones enviadas y recibidas por el navegador o 
browser, con esto se puede visualizar que el protocolo utilizado es 
HTTP y la versión corresponde a HTTP 1.1 empleada con el método 
GET (muestran los datos de forma visible). 

![](/TheusZero/images/post/Redes/redes7.png)

Luego para obtener la IP y el puerto que fue utilizado, se procede a expandir la información o detalles del paquete, en donde se obtiene:

![](/TheusZero/images/post/Redes/redes8.png)

Donde se puede concluir que el puerto utilizado por la terminal host fue el 38844 (Src Port) y el puerto de destino fue el 80 (Dst Port), reservado para el protocolo HTTP del servidor.

El IP de nuestra máquina se puede visualizar como 192.168.236.128 (Src) y el de destino como 200.1.17.3 (Dst).

Los parámetros ingresados en la página index1.html, son utilizados bajo el método GET, tal y como lo muestra Wireshark, sin embargo, se confirma lo que se pudo deducir en un inicio sobre la URL que se está analizando.

A continuación, se puede observar en color rojo, la petición enviada al servidor, y en color azul, la respuesta del mismo, en este caso, la petición del GET.

A continuación, se puede visualizar en el apartado del frame, la cantidad de bytes que se transfirieron en el paquete.

![](/TheusZero/images/post/Redes/redes9.png)

![](/TheusZero/images/post/Redes/redes10.png)

Como se muestra en la imagen la cantidad de bytes transferidos corresponde a un total de 582 bytes, que corresponden a 4656 bits.

Para estimar el tiempo que fue utilizado se utiliza el apartado Time en Wireshark, comparando el tiempo del paquete de envío al servidor y el de respuesta de este, ya que podemos encontrar el paquete con el código de respuesta HTTP 200 OK, en donde se demuestra que la solicitud, en este caso que se utiliza el GET, ha sido realizada con éxito.

![](/TheusZero/images/post/Redes/redes11.png)

En la imagen se muestra que el primer paquete de envío es el N° 46 y el de respuesta es el N°48, por lo tanto, calculando la diferencia entre ellos, se estima un tiempo utilizado de 0.03 [s].

Las conexiones que fueron usadas se deducen bajo la cantidad de paquetes enviados, por lo tanto, en este caso se habla de 4 conexiones utilizadas. 

En el navegador, accedemos al URL: 
> http://ramos.elo.utfsm.cl/~elo322/index2.html 

y se vuelven a completar los datos requeridos:

![](/TheusZero/images/post/Redes/redes12.png)

Volviendo a Wireshark, filtramos los paquetes para el protocolo HTTP, donde obtenemos lo siguiente:

![](/TheusZero/images/post/Redes/redes13.png)

Se puede observar que el protocolo utilizado corresponde a HTTP en su versión 1.1.

Como conocemos el IP de la máquina que se está utilizando, “192.168.236.128”, y el IP del Servidor, “200.1.17.3”, como muestra el apartado de “Source” y “Destination” de Wireshark.

El puerto utilizado por la terminal host fue el 38844 (Src Port) y el puerto de destino fue el 80 (Dst Port), reservado para el protocolo HTTP del servidor.

Se puede observar que el servidor realiza la primera petición GET, seguida de una confirmación y envío de respuesta por parte del servidor.

En este caso el apartado es diferente, debido a que el método empleado será el POST, y para comprobarlo se revisa el código de fuente dónde se encuentran los datos requeridos, donde se observa lo siguiente: 

![](/TheusZero/images/post/Redes/redes14.png)

Sin embargo, también lo corroboraremos con Wireshark, en donde se selecciona el paquete que lleva consigo el método POST, que fue enviado al servidor, obteniendo lo siguiente:

![](/TheusZero/images/post/Redes/redes15.png)

Los parámetros ingresados en la página index2.html, son utilizados bajo el método POST, como se puede apreciar en la antepenúltima línea de la imagen anterior, en donde se visualiza que el método empleado al enviar formulario es POST.

El método POST en webs PHP se caracteriza porque la información no se visualiza como “header” del HTTP request, es decir, no es visible, donde se asume que es “más seguro”, sin embargo, con Wireshark es posible interceptar el paquete para determinar y conocer cuáles fueron los datos entregados.

En el caso de determinar los datos transferidos, en el frame se puede observar lo siguiente:

![](/TheusZero/images/post/Redes/redes15.png)

Entonces, se puede observar que la cantidad de bytes transferidos en el paquete de envío con el método POST corresponden a un total de 649 bytes (5192 bits).

El tiempo estimado que fue utilizado con el paquete con método POST, se hará de forma “distinta” a la que se realizó con el paquete con método GET, en donde tomaremos como referencia la información exacta de la hora que registro Wireshark:

> Paquete de envío con método POST:

![](/TheusZero/images/post/Redes/redes16.png)

> Paquete recibido de parte del servidor (HTTP 200 OK):

![](/TheusZero/images/post/Redes/redes17.png)

Calculando la diferencia entre ambos, es decir, la diferencia de tiempo entre el paquete recibido con el paquete de envío se tiene que el tiempo utilizado estimado es de 0.1 [s] aproximadamente.
Las conexiones utilizadas.

#### Conclusion

Una vez finalizado el desarrollo del informe, se pueden mostrar variadas diferencias entre ambos URL analizados mediante Wireshark, a pesar de que ambos desarrollos se realizaron de manera similar y en ambos casos se requirieron las mismas respuestas.

Analizando ambos casos, se puede demostrar que ambos protocolos utilizados son HTTP y también se utiliza la misma versión de protocolo, que en este caso es HTTP 1.1.

La primera diferencia entre ambos URL es el método que se emplea en ambos, en Index1 se emplea GET en dónde los datos son inmediatamente visibles, en cambio, en Index2 se emplea el método POST, el cual se caracteriza porque los datos no son visibles, entonces se le atribuye la característica de ser “más seguro”, aún así es posible interceptar el paquete para ver los datos que fueron entregados.

Ya que la principal diferencia entre los URL es el método empleado, se pueden comparar sus ventajas y desventajas, en el caso del método POST, su ventaja es el envío de datos de forma invisible y discreta, en cambio en el método GET si un usuario accede a la URL entregada, tendrá la información del otro usuario, es decir, tendrá acceso a los datos entregados y además cuenta con un límite de 2000 caracteres. Hablando de las ventajas que se obtiene al emplear el método GET, se obtiene que el envío de datos codificados desde un “header” del HTTP request va directamente en la URL del navegador por lo que el usuario puede acceder siempre a ésta URL siempre y cuando la guarde o preestablezca en el navegador, en cambio, en el método POST, la información no se almacena en el browser.

En el caso de la IP y los puertos utilizados, se demuestra en el informe que tanto Index1 como Index2 ocupan el mismo IP tanto para el servidor como el IP de la máquina virtual utilizada, además de ambos usar el puerto 80 como puerto de destino para HTTP y el Terminal Host 38844.

La cantidad de bytes transferidos entre ambos URL Index1 e Index2, varía en una cantidad bastante baja de bytes, los cuales transfirieron una cantidad de 582 y 649 bytes respectivamente.

Una vez estimado el tiempo utilizado en ambos, se puede concluir que el tiempo empleado en Index1 es menor al tiempo empleados en Index2.

Finalizando, podemos concluir que los dos URL utilizados, que utilizan el mismo protocolo (HTTP), la misma versión de protocolo (HTTP 1.1), el mismo IP y puertos, pero están empleados con diferentes métodos (GET y POST), generando una variación (diferencia), tanto en bytes transferidos, como en el tiempo empleado y la cantidad de conexiones utilizadas, además permite dar a conocer las grandes diferencias entre el método GET y POST en el análisis mediante Wireshark de ambos URL.

> Nota = 80/100


## Tarea 2:

Esta tarea creo que fue lamas chacota, la hice el mismo dia de la entrega **se me olvido que habia tarea**, por ende, la informacion puede estar un poco desordenada.

#### Introducción
     
En esta tarea, como equipo de trabajo analizaremos cada uno de los protocolos seleccionados, 
     con sus respectivos experimentos respaldados en la información que será entregada mediante 
     el analizador de paquetes y tráfico de red wireshark.  
     
Comenzaremos con el protocolo llamado Dynamic Host Configuration Protocol o más 
     comúnmente DHCP, el cual es una extensión del protocolo Bootstrap (BOOTP) desarrollado 
     en 1985 para conectar dispositivos como terminales y estaciones de trabajo. Su mayor énfasis 
     como protocolo en este laboratorio será experimentar con la capacidad de asignar 
     automáticamente las direcciones de red o IP, realizando configuraciones a los parámetros de 
     red asignables como lo es el DNS y la Máscara de Subred, mediante comandos introducidos 
     en la terminal de una maquina con un sistema operativo Linux. 

Siguiendo con el desarrollo, el próximo protocolo que tocará por analizar corresponderá a 
     ARP o Address Resolution Protocol, este es imprescindible a la hora de convertir las 
     direcciones de protocolo de alto nivel como las direcciones IP a direcciones de red físicas, 
     mediante configuraciones a los parámetros de red, revisando su dirección MAC y realizando 
     un respaldo en el cache del mismo. Este será analizado por wireshark mediante una maquina 
     Windows, para poder ver como actúa este protocolo. 
  
Por último y no menos importante, realizaremos pruebas con comandos Linux y Windows 
     para el protocolo ICMP, el cual se encarga de controlar especialmente los mensajes de error 
     y control necesarios para los sistemas de redes de computadoras, enfocado al envió de 
     paquetes para así, como protocolo, poder analizar si este paquete no puede alcanzar su 
     destino, si su vida ha expirado, si el encabezado lleva un valor no permitido, si es un paquete 
     de eco o respuesta, etc. Los comandos que se utilizaran corresponden a PING y a 
     TRACEROUTE (TRACERT en windows). 

#### Servicio DHCP

Primero empezamos con un reconocimiento de la ip de nuestro equipo y de la configuración 
de red que nuestra maquina posee: 

![](/TheusZero/images/post/Redes/Tarea2/tarea2_1.png)

Ya conocida nuestra IP que corresponde a “192.168.236.128” y que usamos la configuración 
de “eth0” nos disponemos a abrir Wireshark para comenzar a escanear el tráfico de red.

![](/TheusZero/images/post/Redes/Tarea2/tarea2_2.png)

Hacemos la configuración para escanear solamente el tráfico de red 
en “eth0” y abrimos la terminal de nuestro equipo, ya que así lograremos mediante una serie 
de comandos filtrar en wireshark los paquetes hacia y desde nuestra maquina en una solicitud 
dinámica de ip. 

En la terminal se usarán los siguientes comandos:

![](/TheusZero/images/post/Redes/Tarea2/tarea2_3.png)

El comando **dhclient** obtiene una lista de todas las interfaces de red que están configuradas 
en la maquina actual. Para cada interfaz, intenta configurar esta misma utilizando el protocolo 
DHCP para así liberar la IP actual y obtener una nueva desde el servidor DHCP de nuestro 
sistema. 

Primero usaremos el comando **dhclient –r** para borrar cualquier viejo proceso y podemos 
complementarlo con **dhclient –r –v** que agrega un **vervose** para poder imprimir por 
pantalla cada uno de los procesos que ejecuta este comando.

![](/TheusZero/images/post/Redes/Tarea2/tarea2_4.png)

El comando “dhclient -v” genera el servidor para poder obtener la nueva dirección ip, 
haciéndole esta configuración a todas las interfaces activas. En nuestro caso, la interfaz activa 
de nuestra maquina corresponde a “eth0” por lo cual le damos este parámetro a “dhclient” 
para que se ejecute solo en esta interfaz.

![](/TheusZero/images/post/Redes/Tarea2/tarea2_5.png)

Ahora, ya explicado los comandos, comenzamos primero utilizando el comando: 

> dhclient –r 

Ya liberado cualquier tipo de servidor dhclient comenzamos el escaneo con wireshark. 
Cuando wireshark ya este escaneando y no estemos con ningún servidor dhcp activo, 
colocaremos en la terminal el comando: 

> dhclient –v eth0 

De esta forma, le asignaremos una ip a nuestra máquina. 

Abriremos otra terminal para verificar el cambio de ip, en nuestro caso, como utilizamos 
anteriormente el comando para liberar la dirección ip “dhclient –r” deberíamos tener una 
dirección nueva ahora. 

Ya listo y dado el mensaje por pantalla y verificado el cambio de ip, cerraremos o liberaremos 
la ip mediante otro: 

> dhclient –r 

![](/TheusZero/images/post/Redes/Tarea2/tarea2_6.png)

Ahora revisando wireshark y filtrando los paquetes mediante la opción: 

> **bootp** o **udp.port** **==** **67** && **udp.port==68**
 
Como en el comando “dhclient” no especifique un Puerto en específico con el parámetro 
**-p (puerto)**, el comando asume el puerto por default, que corresponde al 68, por lo que 
serviría la segunda opción. En caso de que sea en un puerto especifico, se debe usar el filtro 
**bootp**

![](/TheusZero/images/post/Redes/Tarea2/tarea2_7.png)

Tenemos un total de 5 paquetes DHCP utilizados, correspondientes a: 

> DHCP ACK
> 
> DHCP Discover
> 
> DHCP Offer
> 
> DHCP Release
> 
> DHCP Request 

Para cada uno de estos paquetes se utiliza **UDP**, ya que mirando 
wireshark en el apartado de “Internet Protocol” podemos encontrar lo siguiente:

![](/TheusZero/images/post/Redes/Tarea2/tarea2_8.png)

La dirección ip que fue asignada para nuestra maquina corresponde a la: 

> **192.168.236.132**
 
Como lo muestra wireshark:

![](/TheusZero/images/post/Redes/Tarea2/tarea2_9.png)

#### Protocolo ARP

Primero en la línea de comandos usamos **arp -a** para poder ver cualquier tipo de 
**ARP entry** existente, obteniendo lo siguiente: 

![](/TheusZero/images/post/Redes/Tarea2/tarea2_10.png)

Luego, limpiamos el cache de nuestro navegador, colocamos 
a wireshark a capturar tráfico de red y nos disponemos a buscar páginas web. 
Visitamos diferentes webs, entre ellas se obtuvo lo siguiente en wireshark: 

![](/TheusZero/images/post/Redes/Tarea2/tarea2_11.png)

#### Protocolo ICMP (PING y TRACEROUTE)  

Para analizar el protocolo ICMP se nos pidió que usáramos “Ping” y “Traceroute” para 
analizarlos en wireshark, por lo tanto, comenzamos con un simple ifconfig en la terminal, así 
logramos ver cuál es la ip de nuestra máquina y sus respectivas configuraciones de red.

![](/TheusZero/images/post/Redes/Tarea2/tarea2_12.png)

Para poder realizar un ping en Linux, mediante la terminal ocupamos el comando:

> **ping (options) destination**

Donde “options” serían los parámetros u opciones para realizar el 
ping y “destination” el nombre del DNS o la IP del equipo. 

Para poder realizar un Traceroute en Linux, mediante la terminal ocupamos el comando: 

> **traceroute (options)**

Tambien usamos el comando “nslookup” ya que este realiza una búsqueda DNS inversa (es 
decir, encontrar el nombre de dominio de una determinada dirección IP): 

> **nslookup (dominio)**

Ocuparemos el dominio de **ramos.elo.utfsm.cl** para hacer cada una de las pruebas así que 
por ende usaremos nslookup para conocer la ip del mismo servidor (*aunque wireshark 
también muestra la ip del servidor si se le envía algún paquete a este mismo*).

![](/TheusZero/images/post/Redes/Tarea2/tarea2_13.png)

Ahora, ya especificado el uso de los comandos, toca configurar wireshark de manera básica 
y comenzar a capturar el tráfico.

Primero realizamos el uso del ping. Mandamos un ping al dns 
**ramos.elo.utfsm.cl** y luego directamente a la dirección ip del webserver obteniendo lo 
siguiente:

![](/TheusZero/images/post/Redes/Tarea2/tarea2_14.png)

Obteniendo de wireshark lo siguiente: 

![](/TheusZero/images/post/Redes/Tarea2/tarea2_15.png)

Analizando el paquete “request” que se envió al servidor:

![](/TheusZero/images/post/Redes/Tarea2/tarea2_16.png)

Del paquete request podemos obtener lo siguiente: 

> El paquete tenía un peso de 98 bytes (784 bits) 

> Protocolo ICMP 

> Destino: 200.1.17.3 (IP del servidor) 

> Type: 8 (Echo (ping) Request) 

> Checksum: correcto 

> Tiempo de vida = 64 

> Data enviada: 

![](/TheusZero/images/post/Redes/Tarea2/tarea2_17.png)

Analizaremos el paquete “reply” que se envió como respuesta:

![](/TheusZero/images/post/Redes/Tarea2/tarea2_17.png)

Del paquete request podemos obtener lo siguiente: 

> El paquete tenía un peso de 98 bytes (784 bits) 

> Protocolo ICMP 

> Destino: 192.168.236.128 (IP de nuestra maquina) 

> Type: 0 (Echo (ping) Reply) 

> Checksum: correcto 

> Tiempo de respuesta = 26,5 [ms] 

> Tiempo de vida = 128 

> Data enviada: 

![](/TheusZero/images/post/Redes/Tarea2/tarea2_18.png)

Ahora comenzaremos con “Traceroute”, primero cambiaremos de 
sistema a Windows y usaremos el comando mediante la terminal CMD:

> **C:\Windows\system32> tracert www.solotodo.com**

Obtenemos lo siguiente:

![](/TheusZero/images/post/Redes/Tarea2/tarea2_19.png)

Wireshark: 

![](/TheusZero/images/post/Redes/Tarea2/tarea2_20.png)

> Tipo de mensaje ICMP = Echo (ping) request 

> Tipo de mensaje ICMP = Echo (ping) reply 

#### Conclusión

Durante la ardua investigación, se cumplió el objetivo de identificar y experimentar en un 
laboratorio seguro con los protocolos DHCP, ARP e ICMP. Esta investigación se logró 
gracias a la aplicación Wireshark y mediante comandos en la terminal, usando sistemas 
operativos Linux y Windows, destacando así la importancia de cada uno de los protocolos 
para la administración de las redes de computadoras. 

Como equipo queremos resaltar el uso de los comandos por terminal, ya que en Linux se usó 
mucho la terminal, ingresando cada uno de los comandos requeridos para poder analizar el 
comportamiento de los protocolos o el mismo inicio de cada uno de estos. 

Cabe destacar que algunas pruebas fueron hechas bajo entornos Windows, por algunos 
problemas con las máquinas virtuales Linux, ya que muchas de estas tenían una 
configuración de red de tipo NAT, por lo cual, wireshark registraba el tráfico que realizaba 
la aplicación para las maquinas virtuales.

> Nota = 90/100

## Tarea 3:

En esta tarea nos cagaron rico. Creo que igual fue mi culpa por flojo, deje los ultimos 3 dias para hacer la tarea ya que al leerla de manera rapida pense que seria un simple **encrypt/decrypt**
con **RSA**, pero no fue asi, ya que el lenguaje pedido fue con **Java** y el requerimiento especial estaba demasiado cabron. 

Debias hacer un **encrypt** de un **string** con la llave publica entregada en el aula, crear un socket en el servidor de aragon y mandar el string a este mismo, que el servidor lo lea y le haga el **decrypt** correspondiente y lo mande de vuelta al equipo. 

> al momento de tomar el ramo, era mechon y no estaba familiarizado con Java y el tiempo no fue el suficiente.

**Codigo Socket para servidor**

Este codigo te abre un puerto a la escucha de manera infinita, es decir, si manda la respuesta el servidor seguira a la escucha a menos que este mismo programa sea cortado.

```Python
import java.io.*; 
import java.net.*; 

class TCPServer { 

  public static void main(String argv[]) throws Exception 
    { 

      String clientSentence; 
      String capitalizedSentence; 

      ServerSocket welcomeSocket = new ServerSocket(6789); 
  
      while(true) { 
  
            Socket connectionSocket = welcomeSocket.accept(); 

           BufferedReader inFromClient = 
              new BufferedReader(new
              InputStreamReader(connectionSocket.getInputStream())); 
          
           DataOutputStream  outToClient = 
             new DataOutputStream(connectionSocket.getOutputStream()); 

           clientSentence = inFromClient.readLine(); 

           capitalizedSentence = clientSentence.toUpperCase() + '\n'; 

           outToClient.writeBytes(capitalizedSentence); 
        } 
    } 
} 
```

**Codigo AES para encriptar un string**

Este codigo genera una keysize de 168 para encriptar un string con el metodo AES y crea un archivo en la carpeta actual donde se encuentra ubicado el archivo.
El archivo que crea es el string encriptado, la keysize y la secretkey como tal de la siguiente forma

> StringEncripted,KeySize,SecretKey
 
```Python
import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import java.io.FileWriter;
import java.io.IOException;

public class AES_Encryption {

        private static Cipher cipher = null;

        public static void main(String[] args) throws Exception,IOException {

            FileWriter llave_AES = new FileWriter("TareaRedes.txt");

            // uncomment the following line to add the Provider of choice
            //Security.addProvider(new com.sun.crypto.provider.SunJCE());

            KeyGenerator keyGenerator = KeyGenerator.getInstance("DESede");
            // keysize must be equal to 112 or 168 for this provider
            keyGenerator.init(168);

            SecretKey secretKey = keyGenerator.generateKey();
            cipher = Cipher.getInstance("DESede");

            String plainText = "Java Cryptography Extension";
            System.out.println("Plain Text Before Encryption: " + plainText);

            byte[] plainTextByte = plainText.getBytes("UTF8");
            byte[] encryptedBytes = encrypt(plainTextByte, secretKey);

            String encryptedText = new String(encryptedBytes, "UTF8");
            System.out.println("Encrypted Text After Encryption: " + encryptedText);
            llave_AES.write(encryptedText+","+"168,"+secretKey);
            llave_AES.close();

            /* AQUI COMIENZA A DESENCRYPTAR
            byte[] decryptedBytes = decrypt(encryptedBytes, secretKey);
            String decryptedText = new String(decryptedBytes, "UTF8");
            System.out.println("Decrypted Text After Decryption: " + decryptedText);
            */
        }
        //ENCRIPTACION
        static byte[] encrypt(byte[] plainTextByte, SecretKey secretKey)
                throws Exception {
            cipher.init(Cipher.ENCRYPT_MODE, secretKey);
            byte[] encryptedBytes = cipher.doFinal(plainTextByte);
            return encryptedBytes;
        }
        /*DESENCRIPTACION
        static byte[] decrypt(byte[] encryptedBytes, SecretKey secretKey)
                throws Exception {
            cipher.init(Cipher.DECRYPT_MODE, secretKey);
            byte[] decryptedBytes = cipher.doFinal(encryptedBytes);
            return decryptedBytes;
        }*/
}
```
**Codigo AES - retorna un archivo solo con la llave simetrica - (Este usare creo)**
```Python
import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import java.io.FileWriter;
import java.io.IOException;

public class AES_Encryption {

        private static Cipher cipher = null;

        public static void main(String[] args) throws Exception,IOException {

            FileWriter llave_AES = new FileWriter("TareaRedes.txt");

            // uncomment the following line to add the Provider of choice
            //Security.addProvider(new com.sun.crypto.provider.SunJCE());

            KeyGenerator keyGenerator = KeyGenerator.getInstance("DESede");
            // keysize must be equal to 112 or 168 for this provider
            keyGenerator.init(168);

            SecretKey secretKey = keyGenerator.generateKey();
            cipher = Cipher.getInstance("DESede");

            String plainText = "Java Cryptography Extension";
            System.out.println("Plain Text Before Encryption: " + plainText);

            byte[] plainTextByte = plainText.getBytes("UTF8");
            byte[] encryptedBytes = encrypt(plainTextByte, secretKey);

            String encryptedText = new String(encryptedBytes, "UTF8");
            System.out.println("Encrypted Text After Encryption: " + encryptedText);
            llave_AES.write(encryptedText);
            llave_AES.close();

            /* AQUI COMIENZA A DESENCRYPTAR
            byte[] decryptedBytes = decrypt(encryptedBytes, secretKey);
            String decryptedText = new String(decryptedBytes, "UTF8");
            System.out.println("Decrypted Text After Decryption: " + decryptedText);
            */
        }
        //ENCRIPTACION
        static byte[] encrypt(byte[] plainTextByte, SecretKey secretKey)
                throws Exception {
            cipher.init(Cipher.ENCRYPT_MODE, secretKey);
            byte[] encryptedBytes = cipher.doFinal(plainTextByte);
            return encryptedBytes;
        }
        /*DESENCRIPTACION
        static byte[] decrypt(byte[] encryptedBytes, SecretKey secretKey)
                throws Exception {
            cipher.init(Cipher.DECRYPT_MODE, secretKey);
            byte[] decryptedBytes = cipher.doFinal(encryptedBytes);
            return decryptedBytes;
        }*/
}
```

**Codigo RSA - Generar Llaves Privadas y Publicas**

Este codigo sirve para crear un PATH=RSA/ que guarda los archivos de las llaves privadas y publicas

```Python
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.security.*;
import java.util.Base64;

public class RSA {

    private PrivateKey privateKey;
    private PublicKey publicKey;

    public RSA() throws NoSuchAlgorithmException {
        KeyPairGenerator keyGen = KeyPairGenerator.getInstance("RSA");
        keyGen.initialize(1024);
        KeyPair pair = keyGen.generateKeyPair();
        this.privateKey = pair.getPrivate();
        this.publicKey = pair.getPublic();
    }

    public void writeToFile(String path, byte[] key) throws IOException {
        File f = new File(path);
        f.getParentFile().mkdirs();

        FileOutputStream fos = new FileOutputStream(f);
        fos.write(key);
        fos.flush();
        fos.close();
    }

    public PrivateKey getPrivateKey() {
        return privateKey;
    }

    public PublicKey getPublicKey() {
        return publicKey;
    }

    public static void main(String[] args) throws NoSuchAlgorithmException, IOException {
        RSA keyPairGenerator = new RSA();
        keyPairGenerator.writeToFile("RSA/publicKey", keyPairGenerator.getPublicKey().getEncoded());
        keyPairGenerator.writeToFile("RSA/privateKey", keyPairGenerator.getPrivateKey().getEncoded());
        System.out.println(Base64.getEncoder().encodeToString(keyPairGenerator.getPublicKey().getEncoded()));
        System.out.println(Base64.getEncoder().encodeToString(keyPairGenerator.getPrivateKey().getEncoded()));
    }
}
```

**Codigo RSA - encriptar y desencriptar archivos - arreglado :D**

```Python
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.security.*;
import java.util.Base64;
import javax.crypto.BadPaddingException;
import javax.crypto.Cipher;
import javax.crypto.IllegalBlockSizeException;
import javax.crypto.NoSuchPaddingException;
import java.io.*;
import java.nio.file.Files;
import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.security.spec.PKCS8EncodedKeySpec;
import java.security.spec.X509EncodedKeySpec;

public class AsymmetricCryptography {
    private Cipher cipher;

    public AsymmetricCryptography() throws NoSuchAlgorithmException, NoSuchPaddingException {
        this.cipher = Cipher.getInstance("RSA");
    }

    // https://docs.oracle.com/javase/8/docs/api/java/security/spec/PKCS8EncodedKeySpec.html
    public PrivateKey getPrivate(String filename) throws Exception {
        byte[] keyBytes = Files.readAllBytes(new File(filename).toPath());
        PKCS8EncodedKeySpec spec = new PKCS8EncodedKeySpec(keyBytes);
        KeyFactory kf = KeyFactory.getInstance("RSA");
        return kf.generatePrivate(spec);
    }

    // https://docs.oracle.com/javase/8/docs/api/java/security/spec/X509EncodedKeySpec.html
    public PublicKey getPublic(String filename) throws Exception {
        byte[] keyBytes = Files.readAllBytes(new File(filename).toPath());
        X509EncodedKeySpec spec = new X509EncodedKeySpec(keyBytes);
        KeyFactory kf = KeyFactory.getInstance("RSA");
        return kf.generatePublic(spec);
    }

    public void encryptFile(byte[] input, File output, PrivateKey key)
            throws IOException, GeneralSecurityException {
        this.cipher.init(Cipher.ENCRYPT_MODE, key);
        writeToFile(output, this.cipher.doFinal(input));
    }

    public void decryptFile(byte[] input, File output, PublicKey key)
            throws IOException, GeneralSecurityException {
        this.cipher.init(Cipher.DECRYPT_MODE, key);
        writeToFile(output, this.cipher.doFinal(input));
    }

    private void writeToFile(File output, byte[] toWrite)
            throws IllegalBlockSizeException, BadPaddingException, IOException {
        FileOutputStream fos = new FileOutputStream(output);
        fos.write(toWrite);
        fos.flush();
        fos.close();
    }

    public String encryptText(String msg, PrivateKey key)
            throws NoSuchAlgorithmException, NoSuchPaddingException,
            UnsupportedEncodingException, IllegalBlockSizeException,
            BadPaddingException, InvalidKeyException {
        this.cipher.init(Cipher.ENCRYPT_MODE, key);
        return Base64.getEncoder().encodeToString(cipher.doFinal(msg.getBytes("UTF-8")));
    }

    public String decryptText(String msg, PublicKey key)
            throws InvalidKeyException, UnsupportedEncodingException,
            IllegalBlockSizeException, BadPaddingException {
        this.cipher.init(Cipher.DECRYPT_MODE, key);
        return new String(cipher.doFinal(Base64.getDecoder().decode(msg)), "UTF-8");
    }

    public byte[] getFileInBytes(File f) throws IOException {
        FileInputStream fis = new FileInputStream(f);
        byte[] fbytes = new byte[(int) f.length()];
        fis.read(fbytes);
        fis.close();
        return fbytes;
    }
    public static String muestraContenido(String archivo) throws FileNotFoundException, IOException {
        String cadena;
        FileReader f = new FileReader(archivo);
        BufferedReader b = new BufferedReader(f);
        while((cadena = b.readLine())!=null) {
            String file = cadena;
            return file;
        }
        b.close();
        return cadena;
    }
    public static void main(String[] args) throws Exception {
        AsymmetricCryptography ac = new AsymmetricCryptography();
        PrivateKey privateKey = ac.getPrivate("RSA/privateKey");
        PublicKey publicKey = ac.getPublic("RSA/publicKey");



        String msg = muestraContenido("tarearedes.txt");; //aqui debo ingresar el archivo AES
        String encrypted_msg = ac.encryptText(msg, privateKey);
        String decrypted_msg = ac.decryptText(encrypted_msg, publicKey);
        System.out.println("Original Message: " + msg +
                "\nEncrypted Message: " + encrypted_msg
                + "\nDecrypted Message: " + decrypted_msg);

        if (new File("KeyPair/text.txt").exists()) {
            ac.encryptFile(ac.getFileInBytes(new File("KeyPair/text.txt")),
                    new File("KeyPair/text_encrypted.txt"),privateKey);
            ac.decryptFile(ac.getFileInBytes(new File("KeyPair/text_encrypted.txt")),
                    new File("KeyPair/text_decrypted.txt"), publicKey);
        } else {
            System.out.println("Create a file text.txt under folder KeyPair");
        }
    }
}
```

> **Encriptar Todo**

**Generar una llave simétrica AES**

Aqui se genera un archivo "TareaRedes.txt" que corresponde a la encriptacion de un string a AES, como una llave simetrica.

> El archivo lleva de nombre:
>> TareaRedes.txt
>
>> Largo_Llave.txt

```Python
import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import java.io.FileWriter;
import java.io.IOException;

public class AES_Encryption {

    private static Cipher cipher = null;

    public static void main(String[] args) throws Exception,IOException {

        FileWriter llave_AES = new FileWriter("TareaRedes.txt");
        KeyGenerator keyGenerator = KeyGenerator.getInstance("DESede");
        // keysize must be equal to 112 or 168 for this provider
        keyGenerator.init(168);

        SecretKey secretKey = keyGenerator.generateKey();

        cipher = Cipher.getInstance("DESede");

        String plainText = "Java Cryptography Extension";
        System.out.println("Plain Text Before Encryption: " + plainText);

        byte[] plainTextByte = plainText.getBytes("UTF8");
        byte[] encryptedBytes = encrypt(plainTextByte, secretKey);

        String encryptedText = new String(encryptedBytes, "UTF8");
        System.out.println("Encrypted Text After Encryption: " + encryptedText);
        llave_AES.write(encryptedText);
        llave_AES.close();
        FileWriter largo_Llave = new FileWriter("Largo_LLave.txt");
        largo_Llave.write(String.valueOf(secretKey));
        largo_Llave.close();
    }

    //ENCRIPTACION
    static byte[] encrypt(byte[] plainTextByte, SecretKey secretKey)
            throws Exception {
        cipher.init(Cipher.ENCRYPT_MODE, secretKey);
        byte[] encryptedBytes = cipher.doFinal(plainTextByte);
        return encryptedBytes;
    }
}
```

**Generar una llave privada RSA**

Esto genera un directorio en la carpeta donde se ejecuta el programa, esta carpeta con el nombre de RSA guarda la llave secreta para el equipo

> RSA
>
>> privateKEY 

```Python
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.security.*;
import java.util.Base64;

public class RSA {

    private PrivateKey privateKey;

    public RSA() throws NoSuchAlgorithmException {
        KeyPairGenerator keyGen = KeyPairGenerator.getInstance("RSA");
        keyGen.initialize(1024);
        KeyPair pair = keyGen.generateKeyPair();
        this.privateKey = pair.getPrivate();
    }

    public void writeToFile(String path, byte[] key) throws IOException {
        File f = new File(path);
        f.getParentFile().mkdirs();
        FileOutputStream fos = new FileOutputStream(f);
        fos.write(key);
        fos.flush();
        fos.close();
    }

    public PrivateKey getPrivateKey() {
        return privateKey;
    }


    public static void main(String[] args) throws NoSuchAlgorithmException, IOException {
        RSA keyPairGenerator = new RSA();
        keyPairGenerator.writeToFile("RSA/privateKey", keyPairGenerator.getPrivateKey().getEncoded());
        System.out.println(Base64.getEncoder().encodeToString(keyPairGenerator.getPrivateKey().getEncoded())); //Solo es un print para ver si esta bien, no te lo pasa a base64
    }
}
```
**Encriptar la llave simétrica AES, utilizando la llave pública (disponible en Aula) del AlgoritmoRSA**
 
Este codigo corresponde al ejercicio 2 de la tarea 3, ya que encripta la llave AES con la llave RSA publica y crea un archivo llamado RsaEncyption que corresponde a la llave AES encriptada con la llave publica AES

> El archivo lleva de nombre:
>> RsaEncyption

```Python
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.security.*;
import java.util.Base64;
import javax.crypto.BadPaddingException;
import javax.crypto.Cipher;
import javax.crypto.IllegalBlockSizeException;
import javax.crypto.NoSuchPaddingException;
import java.io.*;
import java.nio.file.Files;
import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.security.spec.PKCS8EncodedKeySpec;
import java.security.spec.X509EncodedKeySpec;

public class AsymmetricCryptography {
    private Cipher cipher;

    public AsymmetricCryptography() throws NoSuchAlgorithmException, NoSuchPaddingException {
        this.cipher = Cipher.getInstance("RSA");
    }

    public PublicKey getPublic(String filename) throws Exception {
        byte[] keyBytes = Files.readAllBytes(new File(filename).toPath());
        X509EncodedKeySpec spec = new X509EncodedKeySpec(keyBytes);
        KeyFactory kf = KeyFactory.getInstance("RSA");
        return kf.generatePublic(spec);
    }

    public void encryptFile(byte[] input, File output, PublicKey key)
            throws IOException, GeneralSecurityException {
        this.cipher.init(Cipher.ENCRYPT_MODE, key);
        writeToFile(output, this.cipher.doFinal(input));
    }
    private void writeToFile(File output, byte[] toWrite)
            throws IllegalBlockSizeException, BadPaddingException, IOException {
        FileOutputStream fos = new FileOutputStream(output);
        fos.write(toWrite);
        fos.flush();
        fos.close();
    }

    public String encryptText(String msg, PublicKey key)
            throws NoSuchAlgorithmException, NoSuchPaddingException,
            UnsupportedEncodingException, IllegalBlockSizeException,
            BadPaddingException, InvalidKeyException {
        this.cipher.init(Cipher.ENCRYPT_MODE, key);
        return Base64.getEncoder().encodeToString(cipher.doFinal(msg.getBytes("UTF-8")));
    }
    public byte[] getFileInBytes(File f) throws IOException {
        FileInputStream fis = new FileInputStream(f);
        byte[] fbytes = new byte[(int) f.length()];
        fis.read(fbytes);
        fis.close();
        return fbytes;
    }
    public static String muestraContenido(String archivo) throws FileNotFoundException, IOException {
        String cadena;
        FileReader f = new FileReader(archivo);
        BufferedReader b = new BufferedReader(f);
        while((cadena = b.readLine())!=null) {
            String file = cadena;
            return file;
        }
        b.close();
        return cadena;
    }
    public static void main(String[] args) throws Exception {
        AsymmetricCryptography ac = new AsymmetricCryptography();
        PublicKey publicKey = ac.getPublic("RSA/publicKey");

        String msg = muestraContenido("tarearedes.txt");; //aqui debo ingresar el archivo AES
        String encrypted_msg = ac.encryptText(msg, publicKey);
        System.out.println("Original Message: " + msg +
                "\nEncrypted Message: " + encrypted_msg);
        FileWriter RsaEncyption =  new FileWriter("RsaEncyption");
        RsaEncyption.write(encrypted_msg);
        RsaEncyption.close();
    }
}
```

> Nota 40/100 **No se JAVAAA aksjdkasjdkajdka xd**

## Certamen 1

#### Link en PDF
[]()

#### Preguntas

#### Desarrollo

## Certamen 2

#### Contexto

Como la evaluacion 2 y 3 fueron online, no tengo el respectivo pdf.

Dejare las preguntas de la siguiente forma:

> a.
>
> b.
>
> c.
>
> d.

La respuesta correcta estara **Indicada Asi** para diferenciarla de las demas.
Cualquier cosa, pueden comentar al final del foro si prefieren que lo cambie, o me lo hacen llegar por interno.

#### Preguntas

**1-** Considere 5000 byte datagrama, es transformado en datagramas mas pequeños (MTU =1500 bytes). El tamaño del último datagrama enviado es:

> a. 1480
>
> b. 940
>
> c. 2980
>
> **d. 560**


#### Verdadero/Falso

#### Desarrollo

## Certamen 3
