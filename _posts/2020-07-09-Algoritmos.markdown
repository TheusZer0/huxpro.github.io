---
layout: post
title: "Algoritmos"
subtitle: 'Resumen de clases y archivos sobre algoritmos 2da parte'
date: 2020-07-09 12:00:00
author: "TheusZero"
header-img: "images/post/algoritmos.png"
catalog: true
comments: true
tags:
  - Programacion
  - USM
  - C
  - Tareas
---

# Algoritmos - Resumen 2020 - Clases de Auat y otras cositas 

## Videos y Lista de reproduccion

> [Clases de AUAT](https://www.youtube.com/watch?v=5vagWigOdG4&list=PLgrda20pniFScjC1SgN-JtdmBZjoX7VaZ)
>
> [Canal con material en espanol](https://www.youtube.com/channel/UCnmq-CGB2lEiwxhpa_Q63qQ/featured)

## Links ricolinos

> [Example Algorithms](https://slideplayer.com/slide/12384811/) resumen y pseudocodigo de los distintos algoritmos del ramo (en ingles)
> [Teoría De La Complejidad Algoritmica](https://es.slideshare.net/rolfpinto/teora-de-la-complejidad-algoritmica)

## Clase 01-07

#### Algoritmos
tipo de tecnologia, como analizar algoritmos, saber que tan eficiente es un algoritmo, comparar algoritmos con **metricas**

#### Ancho de banda **No Internet**
restricciones en los canales de comunicaciones internos que hay en el procesador para que un algoritmo pueda ser ejecutado

#### Tiempo de ejecucion
(el mas estandar) permite conversar con los programadores

#### Uso de memoria
no es tan usado pero refiere a la memoria cache de la memoria ram

> Todas esas corresponden a **metricas** para analizar algun algoritmo y comparar y concluir si un algoritmo es mas eficiente que otro en cuanto al uso de esas mismas metricas, es solo para comparar.

No esta bien hablar de sencillez (no usar como parametro)

> el procesador solo ejecuta una instruccion a la vez (se asume esto), (**monociclo**), (1 instruccion a la vez) y depende de cuantas se usan.

#### Tipos de complejidad

> **Espacial**: cuanta memoria se necesita (no tiene que ver con la memoria de entrada) -> sino, cuanta memoria ocupan los datos, entonces, espacial es cuanta memoria se necesita || **Temporal**: cuanto tiempo requiere nuestro programa para ejecutarse considerando que el procesador ejecuta una sola instruccion a la vez

#### Complejidad espacial

cantidad de memoria que requiere un algoritmo, no se considera la cantidad necesaria para almacenar la entrada, es la cantidad de memoria para ejecutarse, de esta forma es una funcion del tamaño de entrada T(n)

#### Complejidad temporal
es la funcion T(n) que describe la cantidad de tiempo requerido para ejecutar un algoritmo, segun su tamaño de entrada, -> cuanto mas grande sea la entrada mas tiempo se va a necesitar +=mayor. -> cuanto mayor se ya que este nos da la cota superior, el **mejor caso**  y el **caso promedio** no siempre se usan.

> **Complejidad = Complejidad Temporal**

#### Ordenamiento por incersion
ordenamiento por insercion (**Insertion Sort**): (Utilizar un *swap*)

![](/TheusZero/images/post/Algoritmos/insertionsort.png)

> input: elementos de entrada de **An**
> 
> ouput: elementos ordenados de mayor a menor o menor a mayor

![](/TheusZero/images/post/Algoritmos/Analysis+of+Insertion+Sort.png)

#### evaluar complejidad
la complejidad depende del tamano de la entrada (no es lo mismo ordenar 6 elementos que ordenar una cadena ya ordenada o ordenar una cadena de 1000 elemntos), de esa forma, para el insert sort mientras mayor elementos tengas mayor sera la complejidad

> *Hipotesis*= "cada una de las lineas del pseudocodigo es una instruccion (un paso en el procesador)".

con esa hiptesis asumimos que cada linea de codigo requiere un tiempo de ejecucion constante y por eso cada linea puede tardar diferente a otra, debido a bucles o distintos otros factores que puedan afectar.
![](/TheusZero/images/post/Algoritmos/consideracionesInsertSort.png)
![](/TheusZero/images/post/Algoritmos/ExplicadoComplejidad.png)
![](/TheusZero/images/post/Algoritmos/auat1.png)

entonces, teniendo ya la complejidad obtenemos al sumar todo que:

![](/TheusZero/images/post/Algoritmos/ecuacionFinal.png)

#### Mejor-Peor caso

**Mejor caso**: para el insert sort el mejor caso es cuando tiene todos los elemntos ordenados (el arreglo completo ordenado) por lo tanto el while no se ejecuta pero si vale 1.

**Peor caso**:  el arreglo esta en el orden inverso:

![](/TheusZero/images/post/Algoritmos/casos.png)

## Clase 03/07

> El O(n) se considera siempre como el peor caso y toma el valor del N de mayor grado o complejidad en la ecuacuion
>
> El GodOfWar(n) es el mejor caso
>
> El caso promedio es Teta(n)

![](/TheusZero/images/post/Algoritmos/promedio.png)

#### Notacion asintotica 

Si un algoritmo tiene comportamiento lineal, entonces su complejidad puede modelarse por una funcion de tipo *f(n)* **lineal en n**. Si la funcion es **cuadratica** entonces g(n*n).

De esa forma:

![](/TheusZero/images/post/Algoritmos/notacionasintotica.png)

#### divide y conquistaras

la estrategia de minimizacion de complejidad computacional llamada **algoritmo divide y consquistaras** aprovecha la **recursividad** y sus ventajas.

>> **divide** el problema en sub-problemas menores de la misma naturaleza, estos se resuelven implicando un menor costo computacional
>
>> **conquista/conquer** resuelve los sub-problemas de manera **recursiva**, el problema puede quedar aveces tan reducido que se resuelve de manera directa
>
>> **combina/merge** las soluciones a los diferentes subproblemas para obtener la solucion general de nuestro problema

el ejemplo que veremos es el algoritmo de **merge sort** (ordenamiento combinado)

> busqueda y combinacion, donde vamos fragmentando nuestros datos de entrada y trabajamos de manera fractal, es decir, en fragmentos (trabajo dividido)
> divide a lo brusco el input de numeros (o el arreglo)(en potencias de dos), de tal forma que tenemos un menor costo.
> necesitamos mayor numero de memoria para procesar todo pero nos importa el tiempo de ejecucion en realidad, por lo que este divide en 2 el tiempo. (pero hay que tenerlo)
> los sub-problemas son indepenedientes uno de otros

>> **divide** los **n** elementos de la secuencia en dos susecuencias de n/2 elemento cada una
>
>> **conquista**: ordena ambas subsecuencias, de manera recursiva, usando el mismo algoritmo de **merge sort**
>
>> **combina** las dos subsecuencias ordenadas para producir la respuesta buscada, este paso es **crucial** en el algoritmo

#### algoritmo de merge

trabajando de la forma **divide y conquistaras** lo aplicaremos al algoritmo de merge

![](/TheusZero/images/post/Algoritmos/merge.png)
![](/TheusZero/images/post/Algoritmos/mergeCompleto.png)
![](/TheusZero/images/post/Algoritmos/mergeExplicado1.png)

> ahora para dividir y conquistar es diferente

#### merge sort recursividad
![](/TheusZero/images/post/Algoritmos/mergeSortExplicado.png)

#### recurrencia

> cuando un algoritmo contiene llamadas **recursivas** su tiempo de ejecucion se describe con **ecuaciones recurrentes** o de recurrencia

para el caso del algoritmo de divide y conquistaras,
 sea T(n) el tiempo de ejecucion para un problema (por ejemplo el **merge-sort**) de
  tamano **n** de entrada. Si **n** es suficientemente chico, supongamos que n<<c 
  (con **c** constante), entonces el costo promedio(1) y permanece fijo. Pero la estrategia 
  divide y conquistaras, divide el problema en **a** subproblemas, cada uno de tamano 1/b (para el caso de merge-sort, es simplemente 1/2). 
  Entonces cada subproblema, tardara ahora **T(n/b)**, y el algoritmo entero tardara aT(n/b). 
  Si ademas tardamos O(n)(costo maximo, peor caso) en dividir el problema en subproblemas, y C(n) en combinar todas las soluciones, 
  entonces tenemos la siguiente recurrencia:

> resumen: 
>> para el caso de dividir y conquistar tenemos un tiempo de ejucion T(n) el tamano de entrada es n, si este n es tan chico respecto a c (constante dada)entonces el **peor-coso=1** <-> (**O(1)**), esto sucede como ejemplo en el initial sequence del merge-sort, ya que dividimos tanto el problema que el costo computacional para ese elemeto es 1.
>
>> cuando usamos la estrategia de dividir y conquistar se divide el problema en **a** subproblemas, cada uno de estos tiene un tamano de **1/b** (cuadno trabajamos con el merge-sort directamente se divide en la arreglo en la mitad, **1/2**). el costo del subproblemava a ser T(n/b) y el algoritmo entero va a ser de aT(n/b)
>
>> D(n) es el costo en dividir el problema en sub-problemas y C(n) en combinar todas las soluciones, entonces en total todo es:

![](/TheusZero/images/post/Algoritmos/recurrencia.png)

![](/TheusZero/images/post/Algoritmos/Screenshot_2020-08-03.png)


#### recurrencia para el algoritmo de merge sort

>> Divide: cuesta Teta(1)
>
>> Conquista: dividimos el problema de forma recursiva en tamano n/2 (2 partes) cada una con tiempo 2T(n/2)
>
>> Combina: Cuesta Teta(n)

![](/TheusZero/images/post/Algoritmos/recurrenciaMergeSort.png)

#### resolver ecuacion de recurrencia - Arboles recursivos

> **Metodo: Arboles Recursivos**
>> permite resolver problemas de costo computacional de algoritmos que usan llamadas recursivas (recurrencias)
![](/TheusZero/images/post/Algoritmos/metodoArbolesRecursivos.png)

> sin perdida de generalidad, supongamos que **n**es **potencia de dos**
>> se habla de sin perdida de generalidad para determinar que el arbol que se construya sea balanceado y completo y su ultima hoja tendra valor de solo **c**
![](/TheusZero/images/post/Algoritmos/mergeCN.png)
> como trabajamos con arboles binarios podemos decir que hacia abajo, cada una de las lineas seria (log n+1) niveles (recordar que el log es de **base 2** en el ramo)
>> de esa misma forma, el costo computacional final va a ser igual a **cn(log n+1)**
>> **comportamiento asintotico** <=> **T(n) = Teta(n log(n))**

![](/TheusZero/images/post/Algoritmos/arbolbinarioultimo.png)

> Costo computacional de algoritmos visto hasta ahora:
>> insert sort = **Teta(n^2)** (Menor memoria)(Mas tiempo de ejecucion)
>
>> merge sort = **Teta(n log(n))** (recordar base 2) <=> (Mayor memoria)(Menor tiempo de ejecucion)

#### busqueda binaria

> se nos da un arreglo y un numero, si ese numero esta en el arreglo tenemos que devolver la posicion en la que se encuentra el arreglo
>> si vamos buscando elemento por elemento, entonces el costo computacional es de Teta(n) ya que es el peor caso si nos dan el ultimo elementos (**para busqueda lineal**)

![](/TheusZero/images/post/Algoritmos/busquedaBinaria.png)

#### ejemplo analisis de complejidad

![](/TheusZero/images/post/Algoritmos/ejemploComplejidad.png)

## Clase 08/07

#### mas arboles recursivos

![](/TheusZero/images/post/Algoritmos/masEjemplosArbolRecurrente.png)
![](/TheusZero/images/post/Algoritmos/masArbolesRecursivos.png)
 
#### mas divide y conquistaras

> recordar
>> n= entrada (datos)
>
>> 2T(n/2) corresponde a dividir y conquistar || Θ(n) corresponde a Combinar
![](/TheusZero/images/post/Algoritmos/masDivideConquistaras.png)

#### metodo maestro

> el metodo maestro provee cotas para recurrencias de la forma ```T(n) = aT(n/b)+ f(n)``` con 
>la condicion que **a>=1 ; b>1 ; f(n) una funcion previamente conocida**
>> recordar que **a** nos habla de la cantidad de subproblemas (grupos) y **1/b** nos dice la cantiodad de datos que tendra esos subproblemas (2 <=> misma cantdidad de datos).

> [Video que lo explica de pana](https://www.youtube.com/watch?v=VplAn4NHYA0)

> como resumen, debemos sacar el valor **a** y el valor **b** y un valor **c**
>> una vez sacados estos valores, debemos comparar Log(en base **B**) de **A** de un valor **c**
>>> con el resultado de eso, mayor,menor o igual obtenemos una formula para sacar el O(n) es decir, el calculo de la complejidad.  
![](/TheusZero/images/post/Algoritmos/resumenMetodoMaestro.png)

> un caso  en el que no cumple debido a las restricciones, ya que el f(n) no es polimonial(polinomio).
![](/TheusZero/images/post/Algoritmos/noAplica.png)

#### merge sort revisitado
![](/TheusZero/images/post/Algoritmos/mergeSortRevisitado.png)

#### Operaciones elementales

**el tiempo de ejecucion T(n)**: determina el numero de operaciones realizadas por un procesador 

**Operaciones Elementales**: las (OE), son aquellas acciones/instrucciones que el ordenador ejecuta 
en un tiempo acotado por una constante, por ejemplo

> operaciones aritmeticas  y logicas basicas; asignaciones a variables de tipo predefinidopor el compilados, 
>los saltos (llamadas a funciones y/o procedimientos, retornos, etc...)
>> tambien seconsidera la escritura de memoria y la lectura de memoria <=> 1. 

el acceso a estructura indexadas basicas como arrays, a estas operaciones se les considera un costo unitario de 1.
 
#### cotas de complejidad y medidas asintoticas

> **cota superior: notacion big O (omicron)**
>
> dada una funcion f, queremos estudiar aquellas funciones que, a lo sumo, crecen tan rapido como f.al conjunto de estas funciones se les conoce como cota superior de f y lo denominamos como O(f). si f es un algoritmo, entonces el tiempo empleado en ejecutarse nunca sera superior al de su cota
>
>> resumen: el Big O es la cota superior, es decir, el mayor tiempo que puede demorar el algortimo al hablar de **tiempo de ejecucion**, entonces, el big O es igual al peor caso y por ende es la cota superior.

> **cota inferior: notacion omega (godofwar)**
>
> una funcion f que crece tan lentamente como f, es decir, que el conjunto de las funciones que tiene el algoritmo aplica para ser la cota inferior es decir, el mejor caso.

> **orden exacto: notacion Teta <=> Theta**
>
> funciones que crecen asintoticamente de la misma forma, caso promedio, esta entre la cota superior e inferior.

## HeapSort

> el heap es una estructura y el heapsort incorpora esta misma para crear un algoritmo de ordenamiento como el merge-sort y el insert-sort, este heapsort mezcla las ventajas del insertion-sort y del merge-sort

**heapsort**  usa una estructura de datos llamados heap, el heap es un tipo de arreglo que puede representarse mediante un arbol binario. cada nodo del arbol corresponde a un elemento del arreglo. si bien pareciera que el arbol puede construir balanceado y completo, usualmente el subarbol derecho puede carecer de hojas en el mismo nivel que el subarbol izquierdo.

> el primer numero del arreglo, es decir, el numero de la posicion 0 (o 1 en pseudocdigo) sera el nodo raiz del arbol binario para el heapsort

> entonces:
>
>> el nodo raiz es el primer elemento del arreglo
>
>> cada nodo padre resulta de la operacion de [i/2], es decir, la porte entera de i/2.
>> siendo el resultado de esta division, el nodo padre del nodo en el que se esta situando:
> ![](/TheusZero/images/post/Algoritmos/heapTree.png)

> hay dos tipos de heaps binarios: **max-heaps** y **min-heaps**. su diferencia esta en como organizamos la descendencia en el arbol

> para el **max-heap** (imagen anterior), se debe cumplir que para cuaqlueir **nodo i**, se tenga que:
>> el valor o llave almacenado en el indice del arbol, debe cumplir con la condicion de que este, debe ser mayor o igual en tamano al nodo hjjo que tenga
> ![](/TheusZero/images/post/Algoritmos/heepTreeExample.png)

> para el **min-heap** se cumple lo inverso, el valor contenido en el nodo padre, debe ser menor o  igual al valor contenido en el nodo hijo

los **heaps binarios** los usaremos entonces para generar el algoritmo de ordenamiento **heapsort** como tambien para construir **colas de prioridad**.

#### Max-Heapify

> **Max-Heapify**: ordenamiento respecto a la topologia max-heap que se adopta, este procedimiento asegura que el arbol cimple con la topologia, su costo es **O(log n)**
>
> **Build-Max-Heap:** construye un arbol de tipo **max-heap**  este es ek tipo de estructura que usaremos para **sorting**  a partir de un arreglo no ordenado, su costo es lineal **O(n)** (cuando buscamos su costo exacto) o bien **O(n log n)**, sabiendo que el arbol tiene una profundidad de **log n**
>
> **Heapsort**: es el prcedimiento de ordenamiento que estudiaremos y tiene un costo de **O(n log n)**
>
> **Max-Heap-Insert, Heap-Extract-Max, Heap-Increase-Key y  Heap-Maximum**, son prcedimientos que usaremos para generar una pila de prioridades. el costo de cada uno es de O(log n).
> ![](/TheusZero/images/post/Algoritmos/maxHeapify.png)
> ![](/TheusZero/images/post/Algoritmos/maxHeapifyDemostracion.png)

#### Build-Max-Heap

construye el arbol, el unico argumento que recibe es el arreglo

> cambio de variable, y se aplica un for
>> para i = a la longitud o tamano de a dividido entre 2 y hasta 1, es decir, que va de la mitads del arregloy comienza a bajar hasta la posicion 1
>>>se trabaja con la mitad ya que ahi estan los nodos mas importantes como  el nodo padre o raiz

#### heapsort

el heapsort crea un arbol con el maxheap(), una vez ya listo este arbol, el nodo raiz es intercambiado con el ultimo nodo del arbol (el mas chico) y este es **guardado** en otro lugar, es decir, el  largo del nodo se le resta uno, ya que este nodo raiz sale de la strcut como tal y se guarda como primer nodo.

![](/TheusZero/images/post/Algoritmos/heapsortFotosDiapos.png)

finalmente quedaria algo del estilo:

> **[1,2,3,4,7,8,9,10,14,16]**

> HeapSort toma tiempo **O(nlogn)**,ya que el llamado a BUILD-MAX-HEAPtoma tiempo O(n) y cada llamado a MAX-HEAPIFYtomatiempoO(logn).

#### colas de prioridad (Priority queues)- **(Usando Heaps)**:

tipo de estructura de datos utilizada para mantener un conjunto de elementos, de una forma de stack **FILO** (first in last out)

> pero, como son colas de prioridad, a cada dato se le agrega una prioridad donde, mientras mayor sea esta prioridad entonces aunque el dato este en el ultimo lugar sera el primero en salir (comparado con uno que tiene una prioridad baja).

```Python
struct node
{
    int priority;
    int info;
    struct node *next;
}
```
**procedimientos a implementar**

> **Insert(S,x)**: inserta un elemento **x** en el conjunto **S** de elementos de la cosa, lo cual equivale a hacer S=S U {X}
>> el conjunto es el arrego y se inserta un x en el stack
>
> Maximum: retorna el elemento de S con la llave de mayor valor
>> retorna el elemento con mayor prioridad
>> HEAP-MAXIMUM retorna el valor máximo en **tiempo Θ(1)**.
>
> extract-max(s): retorna y remueve el elemento de S que tiene mayor prioridad
>> HEAP-EXTRACT-MAX remueve y retorna el elemento con el valor máximo (operación similar al de HeapSort que vimos antes) en tiempo **O(logn)**
>
> Increase-Key(S,x,k): incrementa la llave (siempre manteniendo la estructura heap, es decir, que los  nodos padres son mayores a los hijos), es decir la prioridad de un elemento x al nuevo valor de k, siendo siempre un valor mayor al anterior es decir, nunca decrementar.
>> HEAP-INCREASE-KEY: primero actualiza el valor de lac lave de A[i] y luego atraviesa un camino entre este nodo hacia el nodo raíz para encontrar un slot apropiado para la clave(prioridad) actualizada y respeta la propiedad base de max-heap. En este proceso, la función compara repetitivamente un elemento con su nodo padre, intercambiando las claves y continuando hasta que se cumpla la propiedad del max-heap. toma tiempo **O(log n)**.
![](/TheusZero/images/post/Algoritmos/colaDePrioridadesFunciones.png)
![](/TheusZero/images/post/Algoritmos/heapIncraseKey.png)
![](/TheusZero/images/post/Algoritmos/heapIncraseKeyFull.png)

**En general, cualquier tipo de operación de cola de prioridades sobre un Heap de n elementos toma tiempo O(log n).**

#### quicksort

> se basa en recursividad y en la estrategia de divide y conquistaras

en la parte de **divide y conquistaras** particiona el arreglo de entrada en 2 partes, es decir, en dos subarreglos.

en la parte de conquistaras se ordena los sub-arreglos antes divididos mediantes llamadas **recursivas** al quicksort

en la parte de **combina**, como los arreglos ya fueron ordenados no hace falta una parte de combinarlos especificamente. 

> tomamos el pivote como el ultimo numero del arreglo, peor coso cuando el arreglo esta ordenando 

![](/TheusZero/images/post/Algoritmos/quickSortExpl.png)

![](/TheusZero/images/post/Algoritmos/QuicksortBacan.png)

> **peor caso**: Ocurre cuando PARTITION produce un sub-problema con n-1 elementos y otro con 0 elementos
>> el tiempo Θ(n^2) ocurre cuando el arreglo de entrada ya se encuentra ordenado completamente
> esto sucede cuando la separacion no es balanceada ya que en cada llamado recursivo toma Teta(n) tiempo
> ![](/TheusZero/images/post/Algoritmos/quickSortPeorCaso.png)

> caso promedio:
> el tiempo de ejecucion esta mucho mas cercano al mejor caso 
>
> ![](/TheusZero/images/post/Algoritmos/quickSortCasoPromedio.png)
>
> ![](/TheusZero/images/post/Algoritmos/quickSortTwo.png)
>
> ![](/TheusZero/images/post/Algoritmos/quickSortOne.png)

> **peor caso O(n^2)** y **caso promedio Teta( n log n )** 

**random quicksorting**

> ![](/TheusZero/images/post/Algoritmos/randomQuickSortResumen.png)

**resumen**
![](/TheusZero/images/post/Algoritmos/resmenQuickSort.png)


#### counting sort 

[explicado bacan](https://www.youtube.com/watch?v=56xR0814To0&list=PLLfC2vEod54KFwQxsBhUvkxICBMCvo7p0&index=3)

![](/TheusZero/images/post/Algoritmos/codigoCountingSort.png)

![](/TheusZero/images/post/Algoritmos/countingSortComplejidad.png)

## Clase 24/07

**el coste de merge sort es Θ(n Log n) en todos los casos**

#### complejidad algoritmica

![](/TheusZero/images/post/Algoritmos/complejidadAlgoritmicaUno.png)

![](/TheusZero/images/post/Algoritmos/complejidadAlgoritmicaDos.png)

#### grafos

**matrices de adyacencia**

![](/TheusZero/images/post/Algoritmos/matricesDeAdyacenciaDirigida.png)


estructura de datos no lineal, es una coleccion de nodos conectados mediante bordes, los conjuntos son finitos.

> la representacion de grafos es G=(V,E), donde V es por vertices y E por edges

otra forma comun de representar los grafos es por una coleccion de listas enlazadas adyacentes o bien usando matrices. Los grafos pueden ser direccionables o no.

un grafo se dice que es esparcido si el **|E|** (la suma de sus edges = la suma de sus lados) es mucho menor que el **|V^2|**. ahora el grafo es denso su el |E| es proximo o cercano al |V^2|

**grafo denso**:
![](/TheusZero/images/post/Algoritmos/grafosDensos.png)

**BFS**

![](/TheusZero/images/post/Algoritmos/bfsImageGris.png)

**Tiempo del algoritmo de BFS**

![](/TheusZero/images/post/Algoritmos/bfsImageGris.png)



#### como sacar los nodos totales de una funcion

![](/TheusZero/images/post/Algoritmos/cantNodosSacar.png)
