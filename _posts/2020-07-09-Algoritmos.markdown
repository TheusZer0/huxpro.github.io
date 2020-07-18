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
