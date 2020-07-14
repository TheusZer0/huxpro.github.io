---
layout: default
title: "NeoTel-Companny"
subtitle: 'Proyecto de Seminario de Programacion - Ley de Cramer'
date: 2020-01-25 12:00:00
author: "TheusZero"
header-img: "images/post/NeoTelCompanny.png"
catalog: true
comments: true
tags:
  - Programacion
  - USM
  - C++
  - Proyectos
  - Tareas
---

# NeoTel-Companny - "Ley de Cramer" - Seminario de Programacion

## Introduccion 

El álgebra lineal es un sistema de ecuaciones lineales que se basan en la utilización de las operaciones aritméticas a través de signos, letras y números para resolver y generalizar un sinfín de problemas orientados a la vida cotidiana y más aún al desarrollo de tecnologías y avances para el área empresarial.

#### Proposito

La compañía NeoTel Companny busca simplificar y racionalizar aquellos ejercicios matemáticos que involucren matrices, vectores, y ecuaciones de tipo lineal con el fin de desarrollar e implementar de manera rápida y eficaz una solución a estos problemas, utilizando una tecnología basada en lenguaje de programación C++ que logra incorporar un algoritmo fundamentado en la renombrada “Ley de Cramer”.

#### Contexto

NeoTel Companny fue fundada durante el 2019, tiene como principal propósito crear y dar forma a tecnologías capaces de agilizar y sintetizar procesos matemáticos de larga duración o desarrollo, a base de software y programas computacionales orientado para empresas y para la vida diaria. 
En este caso NeoTel Companny luego de desarrollar proyectos en lenguajes de programación tales como Python y C++ trae un algoritmo basado en la “Ley de Cramer” que sustenta una forma específica de desarrollar un sistema de matrices o ecuaciones lineales siguiendo una fórmula matemática de características especiales. 
NeoTel Companny utilizando el lenguaje de C++ logra desarrollar un software capaz de resolver matrices y ecuaciones de tipo lineal utilizando un algoritmo basado en la “Ley de Cramer”, también utiliza la plataforma de GitHub para realizar un respaldo y control de versión sobre el programa creado.

#### Referencias

En este apartado se nombra la documentación y bibliografía que fue usada para la realización del proyecto, dentro de la bibliografía utilizada se encuentra: 
•	Algebra lineal y sus aplicaciones, tercera edición (David C. Lay, pag 201 , 2007) 
•	https://www.problemasyecuaciones.com/matrices/ejemplos-regla-Cramer-sistemas-ecuaciones-lineales-problemas-resueltos-2x2-3x3.html
•	https://www.matesfacil.com/BAC/ejercicios-resueltos-CRAMER.html

## Requisitos del Sistema

El software creado por NeoTel Companny, está programado en C++ y recibe el nombre de “C-Cramer” y establece una serie de algoritmos matemáticos basados en la proposición del matemático Gabriel Cramer (1704-1752). Originalmente la llamada “Ley de Cramer” se emplea para matrices y ecuaciones lineales de una dimensión 2x2 y 3x3, sin embargo, el software creado fue personalizado y actualizado para lograr ser funcional en un sistema lineal de matrices de dimensiones de 2x2, 3x3 y 4x4.

#### Requisitos Funcionales

El comportamiento del sistema es amigable para el consumidor, es decir, el software es fácil de usar y emplea métodos sistemáticos basados en opciones que reciba del usuario, ya sea para introducir una variable, como para también terminar y finalizar el sistema.

>RF1	Una vez ejecutado el software en el sistema, se imprime por pantalla para el usuario un menú con diferentes opciones, cada una de esas opciones se eligen con su respectivo número entero (1, 2 o 3). Existen 3 opciones, siendo la primera opción (Opción 1) una matriz 2x2, la segunda opción (Opción 2) una matriz de 3x3 y por último la tercera opción (Opción 3) una matriz de 4x4. Si el usuario ingresa cualquier otro carácter distinto a una de estas opciones, entonces el programa terminará con su respectivo mensaje de adiós.

>RF2	El usuario al elegir una opción, se volverá a imprimir por pantalla los requerimientos, empezando por la primera fila de la matriz o de la ecuación lineal. Si, por ejemplo, el usuario ingresa la Opción 2 (Matriz de 3x3) entonces el programa le pedirá por pantalla el número que acompaña a la incógnita X que correspondería a un número a, luego el número que acompaña a la incógnita Y que correspondería a un número b, luego el número que acompaña a la incógnita Z que correspondería a un número c y por último el valor de esa ecuación lineal completo que corresponde a un valor R (en la imagen corresponde al valor j de la ecuación), quedando en un ejemplo grafico de la siguiente manera. 

![](/TheusZero/images/post/NeoTelCompanny-1.png)

>RF3	 Para introducir números basta con usar cualquier tipo de entero y para agregar un numero negativo seria de la forma –A donde A es el número y el signo (-) se antepone al número egresado. Si el programa detecta que fue introducido un entero no valido (ya sea una letra o algún tipo de carácter no valido) se terminará la opción elegida, pero no el programa y se mostrará un mensaje por pantalla indicando que la operación no fue valida.

>RF4	Por último, el programa realizará los cálculos y mostrará por pantalla los resultados. Siendo estos resultados los valores de cada una de las incógnitas de las matrices o de las ecuaciones lineales.

#### Requisitos de Interfaces

El sistema o software “C-Cramer” entregará como resultados los valores de las incógnitas de cada una de las matrices, en el orden X, Y, Z, W. Los parámetros que el programa recibe son los valores que acompañan a estas incógnitas, siendo estos los valores para las matrices que se resolverán en el programa utilizando la “Ley de Cramer”.
Existe también un parámetro R, cuya funcionalidad seria la del valor de la ecuación lineal. Es decir, el termino al cual se igualan las incógnitas. El software como tal realiza una serie de algoritmos que resuelven matrices aumentadas de tipo “Consistentes” es decir, que si tienen resolución. Sin embargo, el software imprimirá por pantalla un mensaje de “Valor invalido” si logra detectar que la ecuación es “Inconsistente”.
Por lo tanto, para la Opción 1 se le pedirán por pantalla al usuario un total de 6 valores, entre ellos están los valores que acompañan a las incógnitas X, Y con el valor R de la ecuación lineal.
Para la Opción 2 se le pedirán por pantalla al usuario un total de 12 valores, entre ellos están los valores que acompañan a X, Y, Z y el valor R de la ecuación lineal.
Por último, en la Opción 3 se le pedirán por pantalla al usuario un total de 20 valores, entre ellos están los valores que acompañan a X, Y, Z, W y el valor R de la ecuación lineal.
El sistema es capaz de diferir entre valores validos e inválidos cuando el usuario ingresa los enteros correspondientes, terminando así la opción elegía y volviendo al menú para preguntarle al usuario si desea volver a elegir una opción o cerrar el programa.

```vim
Evento 	        Descripción Iniciador	Parámetros	Respuesta
Opción 1	Desarrollo  matriz 2x2	Entero = 1	X,Y,R	Resultado Final
Opción 2	Desarrollo  matriz 3x3	Entero = 2	X,Y,Z,R	Resultado Final
Opción 3	Desarrollo  matriz 4x4	Entero = 3	X,Y,Z,W,R Resultado Final
```

#### Diagrama de Flujos

![](/TheusZero/images/post/NeoTelCompanny-2.png)

## Planificación del Proyecto

#### Objetivo General (Goal)

El proyecto debe ser capaz de solucionar e imprimir el resultado de las ecuaciones lineales o matrices de tipo aumentadas que ingrese el usuario, de dimensiones 2x2, 3x3 y 4x4 mediante la “Ley de Cramer”, con su respectivo desarrollo mediante algoritmos que impone esta ley. Debe ser capaz de identificar si el usuario ingreso algún carácter invalido e imprimir por pantalla un mensaje de error sin que el programa termine. De esta manera, sintetizaremos procesos matemáticos de larga duración o desarrollo entregando un software basado en el lenguaje de programación C++.

#### Objetivos Especificos

>O1. Resolver un sistema de ecuaciones lineales (matrices) de dimensión 2x2 por el método de “Ley de Cramer”

>O2. Resolver un sistema de ecuaciones lineales (matrices) de dimensión 3x3 por el método de “Ley de Cramer”

>O3.	Resolver un sistema de ecuaciones lineales (matrices) de dimensión 4x4 por el método de “Ley de Cramer”

#### Carta Gantt

![](/TheusZero/images/post/NeoTelCompanny-3.png)

## Desarrollo del Proyecto

#### Inicio del Proyecto

Como empresa, comenzamos a investigar en métodos para resolver sistema de ecuaciones lineales que tuvieran que ver con matrices. Una vez encontrado este método denominado como “Ley de Cramer” desarrollamos como primer borrador un programa capaz de resolver una matriz de 2x2, una vez ya aprendido y puesto en un software básico de C++, comenzamos con el desarrollo de la matriz 3x3 y por último la de 4x4, todas funcionando mediante “La ley de Cramer”.

#### Matriz de 2X2

Decidimos trabajar con estructuras y punteros para desarrollar una metodología ordenada y funcional dentro el programa.

La primera estructura que corresponde a la matriz de 2x2 la llamamos “dosXdos” que tiene como valores 6 flotantes que corresponden a números que acompañan a las incógnitas y será el usuario quien ingresará estos valores. 

Dentro de la misma estructura tenemos los Resultados de X e Y, que corresponden a flotantes que reciben el nombre de “ResultadoX” e “ResultadoY” respectivamente. 

Por último, la estructura guarda un valor llamado “ValorPrograma” que corresponde a un flotante, este funciona como indicador de término del programa, es decir, si el usuario ingresa un valor que no corresponde al programa, entonces la variable “ValorPrograma” cambia su valor y por ende termina el software.

Ahora en lo matemático, la llamada “Ley de Cramer” pide encontrar para un sistema de ecuaciones lineales de dimensión 2x2 lo siguiente:

>
>-Determinante del sistema
-Determinante de la incógnita X
-Determinante de la incógnita Y
>

El programa en esta matriz se divide en dos funciones, llamadas “InsertarDos” y “DesarrolloDos”.

La primera función “InsertarDos” pide al usuario cada una de las variables que utilizará para calcular cada determinante, mediante punteros estructuras nombradas anteriormente almacena la información para luego pasar a calcular cada uno de los determinantes.

La segunda función “DesarrolloDos” realiza los desarrollos matemáticos correspondientes usando los valores que fueron almacenados de la primera función “InsertarDos”, así logra calcular cada uno de los determinantes, empezando por el determinante del sistema, luego de la incógnita X y por último el de la incógnita Y.

Por último, la segunda función “DesarrolloDos” divide cada uno de los Determinantes X e Y del Determinante del Sistema para finalizar imprimiendo por pantalla el resultado de cada una de las incógnitas del sistema, de la forma (x, y), siendo “x” el valor de la incógnita X e “y” el valor de la incógnita Y respectivamente.

![](/TheusZero/images/post/NeoTelCompanny-4.png)

![](/TheusZero/images/post/NeoTelCompanny-5.png)

#### Matriz de 3X3

Como empresa, planteamos esta matriz basada en la anterior, ya que aquí solo se le agrega una variable Z a cada una de las ecuaciones de tipo lineal o matrices que calculara el sistema.

Primero creamos una estructura llamada “tresXtres” que tiene como valores a X, Y, Z y R de cada una de las ecuaciones lineales (3 en total). Cada uno de estos valores corresponden a flotantes que acompañan a las incógnitas, es decir, una matriz aumentada.

Dentro de la misma estructura tenemos los Resultados de los Determinantes del Sistema, de X, de Y como también de Z que corresponden a valores flotantes por temas de un desarrollo más completo, ya que los determinantes se sacan utilizando la división, que muchas veces pueden dar valores decimales. Por ultimo en esta misma estructura seguimos teniendo la variable de “ValorPrograma” que corresponde principalmente a un valor 0, pero si este cambia su valor en alguna de las funciones, entonces el programa mandará un mensaje de “Valor invalido” y dejará de usar la opción elegida.

Para la matriz de 3x3 tenemos un total de 2 funciones llamada cada una “InsertarTres” y “DesarrolloTres”

La primera función “InsertarTres” se comporta de manera similar a la función “InsertarDos” ya que es aquí donde pedimos al usuario los datos que usaremos para calcular cada uno de los determinantes, en esta función para la matriz de 3x3 se piden un total de 12 variables obligatorias, que serán almacenadas para luego ser procesadas en la siguiente función.

La segunda función “DesarrolloTres” realiza la “Ley de Cramer” para encontrar las siguientes discriminantes:

>-Determinante del sistema
-Determinante de la incógnita X
-Determinante de la incógnita Y
-Determinante de la incógnita Z
>

Por lo tanto, la función “DesarrolloTres” trabaja con los datos almacenados de la función “InsertarTres’ realizando las operaciones matemáticas que la “Ley de Cramer” indica como necesarias para calcular cada uno de los determinantes.

Por último, se realiza la conversión de esos determinantes encontrados en los valores de cada una de las incógnitas y se imprimen por pantalla de la forma (x, y, z) donde “x” corresponde al valor de la incógnita X, “y” corresponde al valor de la incógnita Y, “z” corresponde al valor de incógnita Z.

![](/TheusZero/images/post/NeoTelCompanny-6.png)

#### Matriz de 4x4

La matriz de 4x4 probamos plantear esta misma como una matriz de 3x3, pero aumentada, debido a esto surgieron un montón de problemas, por lo que decidimos como empresa hacerla desde 0 pero tomando una base parecida a las demás matrices ya hechas.

Primero creamos una estructura llamada “cuatroXcuatro” que tiene como variables a X, Y, Z, W, R de cada una de las ecuaciones lineales o matrices que se planean desarrollar, siendo cada uno de estos flotantes para así poder trabajarlos como decimales.

Dentro de la estructura podemos encontrar flotantes llamados Det(Nombre de la incógnita), que corresponden al determinante de alguna incógnita siento estas incógnitas los valores X, Y, Z, W. Son en total 5 determinantes, considerando también el determinante del sistema. Los 5 determinantes son: DetSistema, DetX, DetY, DetZ y DetW.

Se mantiene dentro de la estructura la idea de “ValorPrograma” que funciona como un alto si el usuario ingresa un valor invalido, adaptándolo también para funcionar si es que la matriz ingresada es inconsistente mandando por pantalla un mensaje de “Valor Invalido” (Se planea una posible actualización en futuras entregas sobre matrices inconsistentes).

Para esta matriz de 4x4 optamos como empresa usar un total de 7 funciones por temas de comodidad y desarrollo, para no repetir algunas variables dinámicas que podrían generar problemas a la larga.

Dentro de estas 7 funciones tenemos como primera función la llamada “InsertarCuatro” que funciona igual que las demás funciones “Insertar” de las otras matrices, es decir, pide por pantalla al usuario los valores que se usaran para calcular la matriz de 4x4, siendo en total de 20 variables de valor flotante, para así poder trabajarlos como decimales.

Luego, dentro de las 7 funciones tenemos 5 que corresponden cada una de ellas a sacar el determinante de cada una de las incógnitas y almacenarlos para así usarlos en una función final llamada “Imprimir”, es decir, tenemos a la función “DesarrolloCuatroSistema” que usa los datos almacenados por la función “InsertarCuatro” para calcular el determinante del sistema, está la función “DesarrolloCuatroX” que corresponde al cálculo del determinante X, después esta “DesarrolloCuatroY” que corresponde a la función que calcula el determinante de Y, así sucesivamente hasta haber calculado los siguientes determinantes en este orden:

>-Determinante del sistema
-Determinante de la incógnita X
-Determinante de la incógnita Y
-Determinante de la incógnita Z
-Determinante de la incógnita W
>

Por último, se encuentra la función imprimir, que imprime los resultados que fueron almacenados de las funciones anteriores, de la forma (X, Y, Z, W). 

#### Termino del Proyecto

Una vez terminado el proyecto, decidimos actualizar la función “int main()” creando bibliotecas de datos con las funciones que fueron creadas, para así poder darle un mejor orden y uso a la información del proyecto. Realizando así el último cambio a la versión 1.0 del proyecto. 

## Conclusión

NeoTel Companny logró crear un algoritmo capaz de resolver sistemas de ecuaciones lineales o matrices de dimensiones 2x2, 3x3 y 4x4 siendo un programa capaz de agilizar un proceso que puede tomar entre 15-30 minutos de manera normal en solo 1 minuto, enfocándose así en solucionar y simplificar muchos procesos basados en la “Ley de Cramer” imprimiendo el resultado correcto de cada una de las variables que se pretendían encontrar.

En esta versión 1.0 se logró crear la base del software siendo así un pie para próximas actualizaciones que podrían facilitar el uso del programa para el consumidor, creando una interfaz gráfica o quizá se podría simplificar el largo del software como tal.

Esta versión 1.0 fue implementada en el lenguaje C++ para el ramo de Seminario de programación de la carrera de Ingeniería civil en Telemática de la Universidad Técnica Federico Santa María.

## Codigo

#### Main.cpp

```vim
#include <iostream>
#include "Kramer.h"
using namespace std;
//Declaraciones de Estructuras
int main() {
    int Tipo;
    D* ejercicioDos = new D;
    T* ejercicioTres = new T;
    C* ejercicioCuatro =  new C;
    cout << "Bienvenido a la Calculadora de matrices de NeoTel Companny."<<endl;
    do {
        cout << "Para elijir que tipo de matriz planea usar,ingrese el numero de la opcion"<<endl<<"opcion 1) matriz 2x2"<<endl;
        cout <<"opcion 2) matrix 3x3"<<endl<<"opcion 3) matrix 4x4"<<endl<<"Introducir cualquier otro caracter distintos a las opciones terminara el programa.";
        cin >> Tipo;
        switch(Tipo) {
            case 1:
                // Desarrollo para un 2x2
                InsertarDos(ejercicioDos);
                if ((ejercicioDos->ValorPrograma)!=1){
                    DesarrolloDos(ejercicioDos);
                    break;
                }
                else{
                    cout<<endl;
                    break;
                }
            case 2:
                InsertarTres(ejercicioTres);
                if ((ejercicioTres->ValorPrograma)!=1){
                    DesarrolloTres(ejercicioTres);
                    break;
                }
                else{
                    cout<<endl;
                    break;
                }
            case 3:
                InsertarCuatro(ejercicioCuatro);
                if ((ejercicioCuatro->ValorPrograma)!=1){
                    DesarrolloCuatroSistema(ejercicioCuatro);
                    break;
                } else{
                    cout<<endl;
                    break;
                }
            default:
                cout << "Gracias por preferir nuestra Calculadora. Hasta pronto!!";
                Tipo= 4;
                break;
        }
        continue;
    }
    while(Tipo != 4);
    return 0;
}
```

#### Kramer.h

```vim
#include <iostream>
#include <string>
using namespace std;
typedef struct dosXdos{
    float x,y,r,X,Y,R;
    float ResultadoX;
    float ResultadoY;
    float ValorPrograma;
}D;
typedef struct tresXtres{
    float x,y,z,r,X,Y,Z,R,aX,aY,aZ,aR;
    float ResultadoX;
    float ResultadoY;
    float ResultadoZ;
    float ValorPrograma;
}T;
typedef struct cuatroXcuatro{
    float x,y,z,w,r,X,Y,Z,W,R,aX,aY,aZ,aW,aR,ax,ay,az,aw,ar;
    float DetSistema;
    float DetX;
    float DetY;
    float DetZ;
    float DetW;
    float ValorPrograma;
}C;
void InsertarDos(D* Ejercicio);
void DesarrolloDos(D* Ejercicio);
//Funcion para Resolver un sistema 3x3
void InsertarTres(T* Ejercicio);
void DesarrolloTres(T* Ejercicio);
//Funcion para Resolver un sistema 4x4
void InsertarCuatro(C* Ejercicio);
void DesarrolloCuatroSistema(C* Ejercicio);
void DesarrolloCuatroX(C* Ejercicio);
void DesarrolloCuatroY(C* Ejercicio);
void DesarrolloCuatroZ(C* Ejercicio);
void DesarrolloCuatroW(C* Ejercicio);
void Imprimir(C* Ejercicio);
```

#### Kramer.cpp

```vim
//
#include "Kramer.h"

void InsertarDos(D* Ejercicio){
        float x, y, r, X, Y, R, ValorPrograma;
        ValorPrograma=0;
        cout << "Ingrese el valor que acompañara al X para la primera ecuacion" << endl;
        cin >> x;
        if(cin.fail()) {
            cin.clear();
            cin.ignore();
            cout << "Valor Invalido" << endl;
            ValorPrograma=1;
            Ejercicio->ValorPrograma=ValorPrograma;
        }
        else {
            Ejercicio->x = x;
        }
        if (ValorPrograma != 1){
            cout << "Ingrese el valor que acompañara al Y para la primera ecuacion" << endl;
            cin >> y;
            if(cin.fail()) {
                cin.clear();
                cin.ignore();
                cout << "Valor Invalido" << endl;
                ValorPrograma=1;
                Ejercicio->ValorPrograma=ValorPrograma;
            }
            else {
                Ejercicio->y = y;
            }
            if (ValorPrograma != 1){
                cout << "Ingrese el valor de la ecuacion" << endl;
                cin >> r;
                if(cin.fail()) {
                    cin.clear();
                    cin.ignore();
                    cout << "Valor Invalido" << endl;
                    ValorPrograma=1;
                    Ejercicio->ValorPrograma=ValorPrograma;
                }
                else{
                    Ejercicio->r = r;
                }
                if (ValorPrograma != 1){
                    cout << "Ingrese el valor que acompañara al X para la segunda ecuacion" << endl;
                    cin >> X;
                    if(cin.fail()) {
                        cin.clear();
                        cin.ignore();
                        cout << "Valor Invalido" << endl;
                        ValorPrograma = 1;
                        Ejercicio->ValorPrograma=ValorPrograma;
                    }
                    else{
                        Ejercicio->X = X;
                    }
                    if (ValorPrograma != 1){
                        cout << "Ingrese el valor que acompañara al Y para la segunda ecuacion" << endl;
                        cin >> Y;
                        if(cin.fail()) {
                            cin.clear();
                            cin.ignore();
                            cout << "Valor Invalido" << endl;
                            ValorPrograma =1;
                            Ejercicio->ValorPrograma=ValorPrograma;
                        }
                        else {
                            Ejercicio->Y = Y;
                        }
                        if (ValorPrograma !=1){
                            cout << "Ingrese el valor de la segunda ecuacion" << endl;
                            cin >> R;
                            if(cin.fail()) {
                                cin.clear();
                                cin.ignore();
                                cout << "Valor Invalido" << endl;
                                ValorPrograma=1;
                                Ejercicio->ValorPrograma=ValorPrograma;
                            }
                            else{
                                Ejercicio->R = R;
                            }
                        }
                    }
            }
            }
        }
}
void DesarrolloDos(D* Ejercicio) {
    //arrays para ordenar los valores
    float uno[3] = {Ejercicio->x, Ejercicio->y, Ejercicio->r};
    float dos[3] = {Ejercicio->X, Ejercicio->Y, Ejercicio->R};
    //Determinante Sistema.
    float determinanteSistema = (uno[0] * dos[1]) - (uno[1] * dos[0]);
    cout << determinanteSistema << endl;
    if (determinanteSistema==0) {
        cout << "el sistema no presenta un formato valido para esta calculadora.";
    }
    else{
        //Determinante de la X.
        float determinanteX = (uno[2] * dos[1]) - (dos[2] * uno[1]);
        cout << determinanteX << endl;
        //Determinante de la Y.
        float determianteY = (uno[0] * dos[2]) - (uno[2] * dos[0]);
        cout << determianteY << endl;
        //Division de los Coeficientes
        float ValorX = (determinanteX / determinanteSistema);
        float ValorY = (determianteY / determinanteSistema);
        float Resultado[2] = {ValorX, ValorY};
        Ejercicio->ResultadoX = Resultado[0];
        Ejercicio->ResultadoY = Resultado[1];
        float resultado[2] = {Ejercicio->ResultadoX,Ejercicio->ResultadoY};
        cout << "el programa ha terminando de operar, los resultados fueron: "<< endl;
        cout << "(" << resultado[0] << "," << resultado[1] << ")" << endl;
        cout << endl << endl;
    }
}
//Funciones3X3
void InsertarTres(T* Ejercicio) {
    float x,y,z,r,X,Y,Z,R,aX,aY,aZ,aR,ValorPrograma;
    ValorPrograma=0;
    cout << "Ingrese el valor que acompañara al X para la primera ecuacion"<<endl;cin >> x;
    if(cin.fail()) {
        cin.clear();
        cin.ignore();
        cout << "Valor Invalido" << endl;
        ValorPrograma=1;
        Ejercicio->ValorPrograma=ValorPrograma;
    }
    else {
        Ejercicio->x = x;
    }
    if (ValorPrograma != 1) {
        cout << "Ingrese el valor que acompañara al Y para la primera ecuacion" << endl;
        cin >> y;
        if(cin.fail()) {
            cin.clear();
            cin.ignore();
            cout << "Valor Invalido" << endl;
            ValorPrograma=1;
            Ejercicio->ValorPrograma=ValorPrograma;
        }
        else {
            Ejercicio->y = y;
        }
        if (ValorPrograma != 1) {
            cout << "Ingrese el valor que acompañara al Z para la primera ecuacion" << endl;
            cin >> z;
            if(cin.fail()) {
                cin.clear();
                cin.ignore();
                cout << "Valor Invalido" << endl;
                ValorPrograma=1;
                Ejercicio->ValorPrograma=ValorPrograma;
            }
            else {
                Ejercicio->z = z;
            }
            if (ValorPrograma != 1){
                cout << "Ingrese el valor de la ecuacion" << endl;
                cin >> r;
                if(cin.fail()) {
                    cin.clear();
                    cin.ignore();
                    cout << "Valor Invalido" << endl;
                    ValorPrograma=1;
                    Ejercicio->ValorPrograma=ValorPrograma;
                }
                else{
                    Ejercicio->r = r;
                }
                if (ValorPrograma != 1){
                    cout << "Ingrese el valor que acompañara al X para la segunda ecuacion" << endl;
                    cin >> X;
                    if(cin.fail()) {
                        cin.clear();
                        cin.ignore();
                        cout << "Valor Invalido" << endl;
                        ValorPrograma=1;
                        Ejercicio->ValorPrograma=ValorPrograma;
                    }
                    else{
                        Ejercicio->X = X;
                    }
                    if (ValorPrograma != 1){
                        cout << "Ingrese el valor que acompañara al Y para la segunda ecuacion" << endl;
                        cin >> Y;
                        if(cin.fail()) {
                            cin.clear();
                            cin.ignore();
                            cout << "Valor Invalido" << endl;
                            ValorPrograma=1;
                            Ejercicio->ValorPrograma=ValorPrograma;
                        }
                        else{
                            Ejercicio->Y = Y;
                        }
                        if (ValorPrograma != 1){
                            cout << "Ingrese el valor que acompañara al Z para la segunda ecuacion" << endl;
                            cin >> Z;
                            if(cin.fail()) {
                                cin.clear();
                                cin.ignore();
                                cout << "Valor Invalido" << endl;
                                ValorPrograma=1;
                                Ejercicio->ValorPrograma=ValorPrograma;
                            }
                            else{
                                Ejercicio->Z = Z;
                            }
                            if (ValorPrograma != 1){
                                cout << "Ingrese el valor de la segunda ecuacion" << endl;
                                cin >> R;
                                if(cin.fail()) {
                                    cin.clear();
                                    cin.ignore();
                                    cout << "Valor Invalido" << endl;
                                    ValorPrograma=1;
                                    Ejercicio->ValorPrograma=ValorPrograma;
                                }
                                else{
                                    Ejercicio->R = R;
                                }
                                if (ValorPrograma != 1){
                                    cout << "Ingrese el valor que acompañara al X para la tercera ecuacion" << endl;
                                    cin >> aX;
                                    if(cin.fail()) {
                                        cin.clear();
                                        cin.ignore();
                                        cout << "Valor Invalido" << endl;
                                        ValorPrograma=1;
                                        Ejercicio->ValorPrograma=ValorPrograma;
                                    }
                                    else{
                                        Ejercicio->aX = aX;
                                    }
                                    if (ValorPrograma != 1){
                                        cout << "Ingrese el valor que acompañara al Y para la tercera ecuacion" << endl;
                                        cin >> aY;
                                        if(cin.fail()) {
                                            cin.clear();
                                            cin.ignore();
                                            cout << "Valor Invalido" << endl;
                                            ValorPrograma=1;
                                            Ejercicio->ValorPrograma=ValorPrograma;
                                        }
                                        else{
                                            Ejercicio->aY = aY;
                                        }
                                        if (ValorPrograma != 1){
                                            cout << "Ingrese el valor que acompañara al Z para la tercera ecuacion" << endl;
                                            cin >> aZ;
                                            if(cin.fail()) {
                                                cin.clear();
                                                cin.ignore();
                                                cout << "Valor Invalido" << endl;
                                                ValorPrograma=1;
                                                Ejercicio->ValorPrograma=ValorPrograma;
                                            }
                                            else{
                                                Ejercicio->aZ = aZ;
                                            }
                                            if (ValorPrograma != 1){
                                                cout << "Ingrese el valor de la tercera ecuacion" << endl;
                                                cin >> aR;
                                                if(cin.fail()) {
                                                    cin.clear();
                                                    cin.ignore();
                                                    cout << "Valor Invalido" << endl;
                                                    ValorPrograma=1;
                                                    Ejercicio->ValorPrograma=ValorPrograma;
                                                }
                                                else{
                                                    Ejercicio->aR = aR;
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
void DesarrolloTres(T* Ejercicio){
    float uno[4] = {Ejercicio->x, Ejercicio->y, Ejercicio->z, Ejercicio->r};
    float dos[4] = {Ejercicio->X, Ejercicio->Y, Ejercicio->Z, Ejercicio->R};
    float tres[4] = {Ejercicio->aX, Ejercicio->aY, Ejercicio->aZ, Ejercicio->aR};
    //determinante Sistema
    float DeterminanteSistemaA =
            (uno[0] * dos[1] * tres[2]) + (dos[0] * tres[1] * uno[2]) + (tres[0] * uno[1] * dos[2]);
    float DeterminanteSistemaB =
            (uno[2] * dos[1] * tres[0]) + (dos[2] * tres[1] * uno[0]) + (tres[2] * uno[1] * dos[0]);
    float DeterminanteSistema = DeterminanteSistemaA - DeterminanteSistemaB;
    if (DeterminanteSistema==0){
        cout << "el sistema no presenta un formato valido para esta calculadora.";
    }
    else {
        //Determinante X
        float DeterminanteXA =
                (uno[3] * dos[1] * tres[2]) + (dos[2] * tres[3] * uno[1]) + (tres[1] * uno[2] * dos[3]);
        float DeterminanteXB =
                (uno[2] * dos[1] * tres[3]) + (dos[2] * tres[1] * uno[3]) + (tres[2] * uno[1] * dos[3]);
        float DeterminanteX = DeterminanteXA - DeterminanteXB;
        //Determinante Y
        float DeterminanteYA =
                (uno[0] * dos[3] * tres[2]) + (dos[2] * tres[0] * uno[3]) + (tres[3] * uno[2] * dos[0]);
        float DeterminanteYB =
                (uno[2] * dos[3] * tres[0]) + (dos[2] * tres[3] * uno[0]) + (tres[2] * uno[3] * dos[0]);
        float DeterminanteY = DeterminanteYA - DeterminanteYB;
        //Determinante Z
        float DeterminanteZA =
                (uno[0] * dos[1] * tres[3]) + (dos[3] * tres[0] * uno[1]) + (tres[1] * uno[3] * dos[0]);
        float DeterminanteZB =
                (uno[3] * dos[1] * tres[0]) + (dos[3] * tres[1] * uno[0]) + (tres[3] * uno[1] * dos[0]);
        float DeterminanteZ = DeterminanteZA - DeterminanteZB;
        //Valores incognitas
        float ValorX = (DeterminanteX / DeterminanteSistema);
        float ValorY = (DeterminanteY / DeterminanteSistema);
        float ValorZ = (DeterminanteZ / DeterminanteSistema);
        float Resultados[3] = {ValorX, ValorY, ValorZ};
        Ejercicio->ResultadoX = Resultados[0];
        Ejercicio->ResultadoY = Resultados[1];
        Ejercicio->ResultadoZ = Resultados[2];
        float resultado[3] = {Ejercicio->ResultadoX, Ejercicio->ResultadoY, Ejercicio->ResultadoZ};
        cout << "el programa ha terminando de operar, los resultados fueron: " << endl;
        cout << "(" << resultado[0] << "," << resultado[1] << "," << resultado[2] << ")" << endl;
        cout << endl << endl;
    }
}
//Funciones4X4
void InsertarCuatro(C* Ejercicio){
    float x,y,z,w,r,X,Y,Z,W,R,aX,aY,aZ,aW,aR,ax,ay,az,aw,ar,ValorPrograma;
    ValorPrograma=0;
    cout << "Ingrese el valor que acompañara al X para la primera ecuacion"<<endl;cin >> x;
    if(cin.fail()) {
        cin.clear();
        cin.ignore();
        cout << "Valor Invalido" << endl;
        ValorPrograma=1;
        Ejercicio->ValorPrograma=ValorPrograma;
    } else{
        Ejercicio->x = x;
    }
    if (ValorPrograma != 1){
        cout << "Ingrese el valor que acompañara al Y para la primera ecuacion"<<endl;cin >> y;
        if(cin.fail()) {
            cin.clear();
            cin.ignore();
            cout << "Valor Invalido" << endl;
            ValorPrograma = 1;
            Ejercicio->ValorPrograma = ValorPrograma;
        } else{
            Ejercicio->y=y;
        }
        if (ValorPrograma != 1){
            cout << "Ingrese el valor que acompañara al Z para la primera ecuacion"<<endl;cin >> z;
            if(cin.fail()) {
                cin.clear();
                cin.ignore();
                cout << "Valor Invalido" << endl;
                ValorPrograma = 1;
                Ejercicio->ValorPrograma = ValorPrograma;
            } else{
                Ejercicio->z=z;
            }
            if  (ValorPrograma != 1){
                cout << "Ingrese el valor que acompañara al W para la primera ecuacion"<<endl;cin >> w;
                if(cin.fail()) {
                    cin.clear();
                    cin.ignore();
                    cout << "Valor Invalido" << endl;
                    ValorPrograma = 1;
                    Ejercicio->ValorPrograma = ValorPrograma;
                } else{
                    Ejercicio->w=w;
                }
                if (ValorPrograma != 1){
                    cout << "Ingrese el valor de la ecuacion"<<endl;cin >> r;
                    if(cin.fail()) {
                        cin.clear();
                        cin.ignore();
                        cout << "Valor Invalido" << endl;
                        ValorPrograma = 1;
                        Ejercicio->ValorPrograma = ValorPrograma;
                    } else{
                        Ejercicio->r=r;
                    }
                    if (ValorPrograma != 1){
                        cout << "Ingrese el valor que acompañara al X para la segunda ecuacion"<<endl;cin >> X;
                        if(cin.fail()) {
                            cin.clear();
                            cin.ignore();
                            cout << "Valor Invalido" << endl;
                            ValorPrograma = 1;
                            Ejercicio->ValorPrograma = ValorPrograma;
                        } else{
                            Ejercicio->X=X;
                        }
                        if (ValorPrograma != 1){
                            cout << "Ingrese el valor que acompañara al Y para la segunda ecuacion"<<endl;cin >> Y;
                            if(cin.fail()) {
                                cin.clear();
                                cin.ignore();
                                cout << "Valor Invalido" << endl;
                                ValorPrograma = 1;
                                Ejercicio->ValorPrograma = ValorPrograma;
                            } else{
                                Ejercicio->Y=Y;
                            }
                            if (ValorPrograma != 1){
                                cout << "Ingrese el valor que acompañara al Z para la segunda ecuacion"<<endl;cin >> Z;
                                if(cin.fail()) {
                                    cin.clear();
                                    cin.ignore();
                                    cout << "Valor Invalido" << endl;
                                    ValorPrograma = 1;
                                    Ejercicio->ValorPrograma = ValorPrograma;
                                } else{
                                    Ejercicio->Z=Z;
                                }
                                if (ValorPrograma != 1){
                                    cout << "Ingrese el valor que acompañara al W para la segunda ecuacion"<<endl;cin >> W;
                                    if(cin.fail()) {
                                        cin.clear();
                                        cin.ignore();
                                        cout << "Valor Invalido" << endl;
                                        ValorPrograma = 1;
                                        Ejercicio->ValorPrograma = ValorPrograma;
                                    } else{
                                        Ejercicio->W=W;
                                    }
                                    if (ValorPrograma != 1){
                                        cout << "Ingrese el valor de la segunda ecuacion"<<endl;cin >> R;
                                        if(cin.fail()) {
                                            cin.clear();
                                            cin.ignore();
                                            cout << "Valor Invalido" << endl;
                                            ValorPrograma = 1;
                                            Ejercicio->ValorPrograma = ValorPrograma;
                                        } else{
                                            Ejercicio->R=R;
                                        }
                                        if (ValorPrograma != 1){
                                            cout << "Ingrese el valor que acompañara al X para la tercera ecuacion"<<endl;cin >> aX;
                                            if(cin.fail()) {
                                                cin.clear();
                                                cin.ignore();
                                                cout << "Valor Invalido" << endl;
                                                ValorPrograma = 1;
                                                Ejercicio->ValorPrograma = ValorPrograma;
                                            } else{
                                                Ejercicio->aX=aX;
                                            }
                                            if (ValorPrograma != 1){
                                                cout << "Ingrese el valor que acompañara al Y para la tercera ecuacion"<<endl;cin >> aY;
                                                if(cin.fail()) {
                                                    cin.clear();
                                                    cin.ignore();
                                                    cout << "Valor Invalido" << endl;
                                                    ValorPrograma = 1;
                                                    Ejercicio->ValorPrograma = ValorPrograma;
                                                } else{
                                                    Ejercicio->aY=aY;
                                                }
                                                if (ValorPrograma != 1){
                                                    cout << "Ingrese el valor que acompañara al Z para la tercera ecuacion"<<endl;cin >> aZ;
                                                    if(cin.fail()) {
                                                        cin.clear();
                                                        cin.ignore();
                                                        cout << "Valor Invalido" << endl;
                                                        ValorPrograma = 1;
                                                        Ejercicio->ValorPrograma = ValorPrograma;
                                                    } else{
                                                        Ejercicio->aZ=aZ;
                                                    }
                                                    if (ValorPrograma != 1){
                                                        cout << "Ingrese el valor que acompañara al W para la tercera ecuacion"<<endl;cin >> aW;
                                                        if(cin.fail()) {
                                                            cin.clear();
                                                            cin.ignore();
                                                            cout << "Valor Invalido" << endl;
                                                            ValorPrograma = 1;
                                                            Ejercicio->ValorPrograma = ValorPrograma;
                                                        } else{
                                                            Ejercicio->aW=aW;
                                                        }
                                                        if (ValorPrograma != 1){
                                                            cout << "Ingrese el valor de la tercera ecuacion"<<endl;cin >> aR;
                                                            if(cin.fail()) {
                                                                cin.clear();
                                                                cin.ignore();
                                                                cout << "Valor Invalido" << endl;
                                                                ValorPrograma = 1;
                                                                Ejercicio->ValorPrograma = ValorPrograma;
                                                            } else{
                                                                Ejercicio->aR=aR;
                                                            }
                                                            if (ValorPrograma != 1){
                                                                cout << "Ingrese el valor que acompañara al X para la cuarta ecuacion"<<endl;cin >> ax;
                                                                if(cin.fail()) {
                                                                    cin.clear();
                                                                    cin.ignore();
                                                                    cout << "Valor Invalido" << endl;
                                                                    ValorPrograma = 1;
                                                                    Ejercicio->ValorPrograma = ValorPrograma;
                                                                } else{
                                                                    Ejercicio->ax=ax;
                                                                }
                                                                if (ValorPrograma != 1){
                                                                    cout << "Ingrese el valor que acompañara al Y para la cuarta ecuacion"<<endl;cin >> ay;
                                                                    if(cin.fail()) {
                                                                        cin.clear();
                                                                        cin.ignore();
                                                                        cout << "Valor Invalido" << endl;
                                                                        ValorPrograma = 1;
                                                                        Ejercicio->ValorPrograma = ValorPrograma;
                                                                    } else{
                                                                        Ejercicio->ay=ay;
                                                                    }
                                                                    if (ValorPrograma != 1){
                                                                        cout << "Ingrese el valor que acompañara al Z para la cuarta ecuacion"<<endl;cin >> az;
                                                                        if(cin.fail()) {
                                                                            cin.clear();
                                                                            cin.ignore();
                                                                            cout << "Valor Invalido" << endl;
                                                                            ValorPrograma = 1;
                                                                            Ejercicio->ValorPrograma = ValorPrograma;
                                                                        } else {
                                                                            Ejercicio->az=az;
                                                                        }
                                                                        if (ValorPrograma != 1){
                                                                            cout << "Ingrese el valor que acompañara al W para la cuarta ecuacion"<<endl;cin >> aw;
                                                                            if(cin.fail()) {
                                                                                cin.clear();
                                                                                cin.ignore();
                                                                                cout << "Valor Invalido" << endl;
                                                                                ValorPrograma = 1;
                                                                                Ejercicio->ValorPrograma = ValorPrograma;
                                                                            } else{
                                                                                Ejercicio->aw=aw;
                                                                            }
                                                                            if (ValorPrograma != 1){
                                                                                cout << "Ingrese el valor para la cuarta ecuacion"<<endl;cin >> ar;
                                                                                if(cin.fail()) {
                                                                                    cin.clear();
                                                                                    cin.ignore();
                                                                                    cout << "Valor Invalido" << endl;
                                                                                    ValorPrograma = 1;
                                                                                    Ejercicio->ValorPrograma = ValorPrograma;
                                                                                }
                                                                                else{
                                                                                    Ejercicio->ar=ar;
                                                                                }
                                                                            }
                                                                        }
                                                                    }
                                                                }
                                                            }
                                                        }
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
void DesarrolloCuatroSistema(C* Ejercicio){
    //Determinante el sistema
    float FilaUno[4] = {Ejercicio->x,Ejercicio->y,Ejercicio->z,Ejercicio->w};
    float UnoFilaUno[5] = {Ejercicio->Y,Ejercicio->Z,Ejercicio->W,Ejercicio->Y,Ejercicio->Z};
    float UnoFilaDos[5] = {Ejercicio->aY,Ejercicio->aZ,Ejercicio->aW,Ejercicio->aY,Ejercicio->aZ};
    float UnoFilaTres[5] = {Ejercicio->ay,Ejercicio->az,Ejercicio->aw,Ejercicio->ay,Ejercicio->az};
    float UnoDiagonal= ((UnoFilaUno[0]*UnoFilaDos[1]*UnoFilaTres[2])+(UnoFilaUno[1]*UnoFilaDos[2]*UnoFilaTres[3])+(UnoFilaUno[2]*UnoFilaDos[3]*UnoFilaTres[4])) - ((UnoFilaUno[4]*UnoFilaDos[3]*UnoFilaTres[2])+(UnoFilaUno[3]*UnoFilaDos[2]*UnoFilaTres[1])+(UnoFilaUno[2]*UnoFilaDos[1]*UnoFilaTres[0]));
    float DosFilaUno[5] = {Ejercicio->X,Ejercicio->Z,Ejercicio->W,Ejercicio->X,Ejercicio->Z};
    float DosFilaDos[5] = {Ejercicio->aX,Ejercicio->aZ,Ejercicio->aW,Ejercicio->aX,Ejercicio->aZ};
    float DosFilaTres[5] = {Ejercicio->ax,Ejercicio->az,Ejercicio->aw,Ejercicio->ax,Ejercicio->az};
    float DosDiagonal= ((DosFilaUno[0]*DosFilaDos[1]*DosFilaTres[2])+(DosFilaUno[1]*DosFilaDos[2]*DosFilaTres[3])+(DosFilaUno[2]*DosFilaDos[3]*DosFilaTres[4])) - ((DosFilaUno[4]*DosFilaDos[3]*DosFilaTres[2])+(DosFilaUno[3]*DosFilaDos[2]*DosFilaTres[1])+(DosFilaUno[2]*DosFilaDos[1]*DosFilaTres[0]));
    float TresFilaUno[5] = {Ejercicio->X,Ejercicio->Y,Ejercicio->W,Ejercicio->X,Ejercicio->Y};
    float TresFilaDos[5] = {Ejercicio->aX,Ejercicio->aY,Ejercicio->aW,Ejercicio->aX,Ejercicio->aY};
    float TresFilaTres[5] = {Ejercicio->ax,Ejercicio->ay,Ejercicio->aw,Ejercicio->ax,Ejercicio->ay};
    float TresDiagonal= ((TresFilaUno[0]*TresFilaDos[1]*TresFilaTres[2])+(TresFilaUno[1]*TresFilaDos[2]*TresFilaTres[3])+(TresFilaUno[2]*TresFilaDos[3]*TresFilaTres[4])) - ((TresFilaUno[4]*TresFilaDos[3]*TresFilaTres[2])+(TresFilaUno[3]*TresFilaDos[2]*TresFilaTres[1])+(TresFilaUno[2]*TresFilaDos[1]*TresFilaTres[0]));
    float CuatroFilaUno[5] = {Ejercicio->X,Ejercicio->Y,Ejercicio->Z,Ejercicio->X,Ejercicio->Y};
    float CuatroFilaDos[5] = {Ejercicio->aX,Ejercicio->aY,Ejercicio->aZ,Ejercicio->aX,Ejercicio->aY};
    float CuatroFilaTres[5] = {Ejercicio->ax,Ejercicio->ay,Ejercicio->az,Ejercicio->ax,Ejercicio->ay};
    float CuatroDiagonal= ((CuatroFilaUno[0]*CuatroFilaDos[1]*CuatroFilaTres[2])+(CuatroFilaUno[1]*CuatroFilaDos[2]*CuatroFilaTres[3])+(CuatroFilaUno[2]*CuatroFilaDos[3]*CuatroFilaTres[4])) - ((CuatroFilaUno[4]*CuatroFilaDos[3]*CuatroFilaTres[2])+(CuatroFilaUno[3]*CuatroFilaDos[2]*CuatroFilaTres[1])+(CuatroFilaUno[2]*CuatroFilaDos[1]*CuatroFilaTres[0]));
    float ResultadoUno = ((FilaUno[0]*UnoDiagonal)+(FilaUno[1]*DosDiagonal*-1)+(FilaUno[2]*TresDiagonal*1)+(FilaUno[3]*CuatroDiagonal*-1));
    cout<<"El determinante del sistema corresponde a: "<<ResultadoUno<<endl;
    Ejercicio->DetSistema=ResultadoUno;
    cout<<"El determinante del sistema es: "<< ResultadoUno<<endl;
    DesarrolloCuatroX(Ejercicio);
}
void DesarrolloCuatroX(C* Ejercicio){
    float FilaUno[4] = {Ejercicio->r,Ejercicio->y,Ejercicio->z,Ejercicio->w};
    float UnoFilaUno[5] = {Ejercicio->Y,Ejercicio->Z,Ejercicio->W,Ejercicio->Y,Ejercicio->Z};
    float UnoFilaDos[5] = {Ejercicio->aY,Ejercicio->aZ,Ejercicio->aW,Ejercicio->aY,Ejercicio->aZ};
    float UnoFilaTres[5] = {Ejercicio->ay,Ejercicio->az,Ejercicio->aw,Ejercicio->ay,Ejercicio->az};
    float UnoDiagonal= ((UnoFilaUno[0]*UnoFilaDos[1]*UnoFilaTres[2])+(UnoFilaUno[1]*UnoFilaDos[2]*UnoFilaTres[3])+(UnoFilaUno[2]*UnoFilaDos[3]*UnoFilaTres[4])) - ((UnoFilaUno[4]*UnoFilaDos[3]*UnoFilaTres[2])+(UnoFilaUno[3]*UnoFilaDos[2]*UnoFilaTres[1])+(UnoFilaUno[2]*UnoFilaDos[1]*UnoFilaTres[0]));
    float DosFilaUno[5] = {Ejercicio->R,Ejercicio->Z,Ejercicio->W,Ejercicio->R,Ejercicio->Z};
    float DosFilaDos[5] = {Ejercicio->aR,Ejercicio->aZ,Ejercicio->aW,Ejercicio->aR,Ejercicio->aZ};
    float DosFilaTres[5] = {Ejercicio->ar,Ejercicio->az,Ejercicio->aw,Ejercicio->ar,Ejercicio->az};
    float DosDiagonal= ((DosFilaUno[0]*DosFilaDos[1]*DosFilaTres[2])+(DosFilaUno[1]*DosFilaDos[2]*DosFilaTres[3])+(DosFilaUno[2]*DosFilaDos[3]*DosFilaTres[4])) - ((DosFilaUno[4]*DosFilaDos[3]*DosFilaTres[2])+(DosFilaUno[3]*DosFilaDos[2]*DosFilaTres[1])+(DosFilaUno[2]*DosFilaDos[1]*DosFilaTres[0]));
    float TresFilaUno[5] = {Ejercicio->R,Ejercicio->Y,Ejercicio->W,Ejercicio->R,Ejercicio->Y};
    float TresFilaDos[5] = {Ejercicio->aR,Ejercicio->aY,Ejercicio->aW,Ejercicio->aR,Ejercicio->aY};
    float TresFilaTres[5] = {Ejercicio->ar,Ejercicio->ay,Ejercicio->aw,Ejercicio->ar,Ejercicio->ay};
    float TresDiagonal= ((TresFilaUno[0]*TresFilaDos[1]*TresFilaTres[2])+(TresFilaUno[1]*TresFilaDos[2]*TresFilaTres[3])+(TresFilaUno[2]*TresFilaDos[3]*TresFilaTres[4])) - ((TresFilaUno[4]*TresFilaDos[3]*TresFilaTres[2])+(TresFilaUno[3]*TresFilaDos[2]*TresFilaTres[1])+(TresFilaUno[2]*TresFilaDos[1]*TresFilaTres[0]));
    float CuatroFilaUno[5] = {Ejercicio->R,Ejercicio->Y,Ejercicio->Z,Ejercicio->R,Ejercicio->Y};
    float CuatroFilaDos[5] = {Ejercicio->aR,Ejercicio->aY,Ejercicio->aZ,Ejercicio->aR,Ejercicio->aY};
    float CuatroFilaTres[5] = {Ejercicio->ar,Ejercicio->ay,Ejercicio->az,Ejercicio->ar,Ejercicio->ay};
    float CuatroDiagonal= ((CuatroFilaUno[0]*CuatroFilaDos[1]*CuatroFilaTres[2])+(CuatroFilaUno[1]*CuatroFilaDos[2]*CuatroFilaTres[3])+(CuatroFilaUno[2]*CuatroFilaDos[3]*CuatroFilaTres[4])) - ((CuatroFilaUno[4]*CuatroFilaDos[3]*CuatroFilaTres[2])+(CuatroFilaUno[3]*CuatroFilaDos[2]*CuatroFilaTres[1])+(CuatroFilaUno[2]*CuatroFilaDos[1]*CuatroFilaTres[0]));
    float ResultadoX = ((FilaUno[0]*UnoDiagonal)+(FilaUno[1]*DosDiagonal*-1)+(FilaUno[2]*TresDiagonal*1)+(FilaUno[3]*CuatroDiagonal*-1));
    cout<<"El determinante de X es: "<< ResultadoX<<endl;
    Ejercicio->DetX=ResultadoX;
    DesarrolloCuatroY(Ejercicio);
}
void DesarrolloCuatroY(C* Ejercicio){
    float FilaUno[4] = {Ejercicio->x,Ejercicio->r,Ejercicio->z,Ejercicio->w};
    float UnoFilaUno[5] = {Ejercicio->R,Ejercicio->Z,Ejercicio->W,Ejercicio->R,Ejercicio->Z};
    float UnoFilaDos[5] = {Ejercicio->aR,Ejercicio->aZ,Ejercicio->aW,Ejercicio->aR,Ejercicio->aZ};
    float UnoFilaTres[5] = {Ejercicio->ar,Ejercicio->az,Ejercicio->aw,Ejercicio->ar,Ejercicio->az};
    float UnoDiagonal= ((UnoFilaUno[0]*UnoFilaDos[1]*UnoFilaTres[2])+(UnoFilaUno[1]*UnoFilaDos[2]*UnoFilaTres[3])+(UnoFilaUno[2]*UnoFilaDos[3]*UnoFilaTres[4])) - ((UnoFilaUno[4]*UnoFilaDos[3]*UnoFilaTres[2])+(UnoFilaUno[3]*UnoFilaDos[2]*UnoFilaTres[1])+(UnoFilaUno[2]*UnoFilaDos[1]*UnoFilaTres[0]));
    float DosFilaUno[5] = {Ejercicio->X,Ejercicio->Z,Ejercicio->W,Ejercicio->X,Ejercicio->Z};
    float DosFilaDos[5] = {Ejercicio->aX,Ejercicio->aZ,Ejercicio->aW,Ejercicio->aX,Ejercicio->aZ};
    float DosFilaTres[5] = {Ejercicio->ax,Ejercicio->az,Ejercicio->aw,Ejercicio->ax,Ejercicio->az};
    float DosDiagonal= ((DosFilaUno[0]*DosFilaDos[1]*DosFilaTres[2])+(DosFilaUno[1]*DosFilaDos[2]*DosFilaTres[3])+(DosFilaUno[2]*DosFilaDos[3]*DosFilaTres[4])) - ((DosFilaUno[4]*DosFilaDos[3]*DosFilaTres[2])+(DosFilaUno[3]*DosFilaDos[2]*DosFilaTres[1])+(DosFilaUno[2]*DosFilaDos[1]*DosFilaTres[0]));
    float TresFilaUno[5] = {Ejercicio->X,Ejercicio->R,Ejercicio->W,Ejercicio->X,Ejercicio->R};
    float TresFilaDos[5] = {Ejercicio->aX,Ejercicio->aR,Ejercicio->aW,Ejercicio->aX,Ejercicio->aR};
    float TresFilaTres[5] = {Ejercicio->ax,Ejercicio->ar,Ejercicio->aw,Ejercicio->ax,Ejercicio->ar};
    float TresDiagonal= ((TresFilaUno[0]*TresFilaDos[1]*TresFilaTres[2])+(TresFilaUno[1]*TresFilaDos[2]*TresFilaTres[3])+(TresFilaUno[2]*TresFilaDos[3]*TresFilaTres[4])) - ((TresFilaUno[4]*TresFilaDos[3]*TresFilaTres[2])+(TresFilaUno[3]*TresFilaDos[2]*TresFilaTres[1])+(TresFilaUno[2]*TresFilaDos[1]*TresFilaTres[0]));
    float CuatroFilaUno[5] = {Ejercicio->X,Ejercicio->R,Ejercicio->Z,Ejercicio->X,Ejercicio->R};
    float CuatroFilaDos[5] = {Ejercicio->aX,Ejercicio->aR,Ejercicio->aZ,Ejercicio->aX,Ejercicio->aR};
    float CuatroFilaTres[5] = {Ejercicio->ax,Ejercicio->ar,Ejercicio->az,Ejercicio->ax,Ejercicio->ar};
    float CuatroDiagonal= ((CuatroFilaUno[0]*CuatroFilaDos[1]*CuatroFilaTres[2])+(CuatroFilaUno[1]*CuatroFilaDos[2]*CuatroFilaTres[3])+(CuatroFilaUno[2]*CuatroFilaDos[3]*CuatroFilaTres[4])) - ((CuatroFilaUno[4]*CuatroFilaDos[3]*CuatroFilaTres[2])+(CuatroFilaUno[3]*CuatroFilaDos[2]*CuatroFilaTres[1])+(CuatroFilaUno[2]*CuatroFilaDos[1]*CuatroFilaTres[0]));
    float ResultadoY = ((FilaUno[0]*UnoDiagonal)+(FilaUno[1]*DosDiagonal*-1)+(FilaUno[2]*TresDiagonal*1)+(FilaUno[3]*CuatroDiagonal*-1));
    cout<<"El Determinante de Y es: "<<ResultadoY<<endl;
    Ejercicio->DetY=ResultadoY;
    DesarrolloCuatroZ(Ejercicio);
}
void DesarrolloCuatroZ(C* Ejercicio){
    float FilaUno[4] = {Ejercicio->x,Ejercicio->y,Ejercicio->r,Ejercicio->w};
    float UnoFilaUno[5] = {Ejercicio->Y,Ejercicio->R,Ejercicio->W,Ejercicio->Y,Ejercicio->R};
    float UnoFilaDos[5] = {Ejercicio->aY,Ejercicio->aR,Ejercicio->aW,Ejercicio->aY,Ejercicio->aR};
    float UnoFilaTres[5] = {Ejercicio->ay,Ejercicio->ar,Ejercicio->aw,Ejercicio->ay,Ejercicio->ar};
    float UnoDiagonal= ((UnoFilaUno[0]*UnoFilaDos[1]*UnoFilaTres[2])+(UnoFilaUno[1]*UnoFilaDos[2]*UnoFilaTres[3])+(UnoFilaUno[2]*UnoFilaDos[3]*UnoFilaTres[4])) - ((UnoFilaUno[4]*UnoFilaDos[3]*UnoFilaTres[2])+(UnoFilaUno[3]*UnoFilaDos[2]*UnoFilaTres[1])+(UnoFilaUno[2]*UnoFilaDos[1]*UnoFilaTres[0]));
    float DosFilaUno[5] = {Ejercicio->X,Ejercicio->R,Ejercicio->W,Ejercicio->X,Ejercicio->R};
    float DosFilaDos[5] = {Ejercicio->aX,Ejercicio->aR,Ejercicio->aW,Ejercicio->aX,Ejercicio->aR};
    float DosFilaTres[5] = {Ejercicio->ax,Ejercicio->ar,Ejercicio->aw,Ejercicio->ax,Ejercicio->ar};
    float DosDiagonal= ((DosFilaUno[0]*DosFilaDos[1]*DosFilaTres[2])+(DosFilaUno[1]*DosFilaDos[2]*DosFilaTres[3])+(DosFilaUno[2]*DosFilaDos[3]*DosFilaTres[4])) - ((DosFilaUno[4]*DosFilaDos[3]*DosFilaTres[2])+(DosFilaUno[3]*DosFilaDos[2]*DosFilaTres[1])+(DosFilaUno[2]*DosFilaDos[1]*DosFilaTres[0]));
    float TresFilaUno[5] = {Ejercicio->X,Ejercicio->Y,Ejercicio->W,Ejercicio->X,Ejercicio->Y};
    float TresFilaDos[5] = {Ejercicio->aX,Ejercicio->aY,Ejercicio->aW,Ejercicio->aX,Ejercicio->aY};
    float TresFilaTres[5] = {Ejercicio->ax,Ejercicio->ay,Ejercicio->aw,Ejercicio->ax,Ejercicio->ay};
    float TresDiagonal= ((TresFilaUno[0]*TresFilaDos[1]*TresFilaTres[2])+(TresFilaUno[1]*TresFilaDos[2]*TresFilaTres[3])+(TresFilaUno[2]*TresFilaDos[3]*TresFilaTres[4])) - ((TresFilaUno[4]*TresFilaDos[3]*TresFilaTres[2])+(TresFilaUno[3]*TresFilaDos[2]*TresFilaTres[1])+(TresFilaUno[2]*TresFilaDos[1]*TresFilaTres[0]));
    float CuatroFilaUno[5] = {Ejercicio->X,Ejercicio->Y,Ejercicio->R,Ejercicio->X,Ejercicio->Y};
    float CuatroFilaDos[5] = {Ejercicio->aX,Ejercicio->aY,Ejercicio->aR,Ejercicio->aX,Ejercicio->aY};
    float CuatroFilaTres[5] = {Ejercicio->ax,Ejercicio->ay,Ejercicio->ar,Ejercicio->ax,Ejercicio->ay};
    float CuatroDiagonal= ((CuatroFilaUno[0]*CuatroFilaDos[1]*CuatroFilaTres[2])+(CuatroFilaUno[1]*CuatroFilaDos[2]*CuatroFilaTres[3])+(CuatroFilaUno[2]*CuatroFilaDos[3]*CuatroFilaTres[4])) - ((CuatroFilaUno[4]*CuatroFilaDos[3]*CuatroFilaTres[2])+(CuatroFilaUno[3]*CuatroFilaDos[2]*CuatroFilaTres[1])+(CuatroFilaUno[2]*CuatroFilaDos[1]*CuatroFilaTres[0]));
    float ResultadoZ = ((FilaUno[0]*UnoDiagonal)+(FilaUno[1]*DosDiagonal*-1)+(FilaUno[2]*TresDiagonal*1)+(FilaUno[3]*CuatroDiagonal*-1));
    cout<<"El Determinante de Z es: "<<ResultadoZ<<endl;
    Ejercicio->DetZ=ResultadoZ;
    DesarrolloCuatroW(Ejercicio);
}
void DesarrolloCuatroW(C* Ejercicio){
    float FilaUno[4] = {Ejercicio->x,Ejercicio->y,Ejercicio->z,Ejercicio->r};
    float UnoFilaUno[5] = {Ejercicio->Y,Ejercicio->Z,Ejercicio->R,Ejercicio->Y,Ejercicio->Z};
    float UnoFilaDos[5] = {Ejercicio->aY,Ejercicio->aZ,Ejercicio->aR,Ejercicio->aY,Ejercicio->aZ};
    float UnoFilaTres[5] = {Ejercicio->ay,Ejercicio->az,Ejercicio->ar,Ejercicio->ay,Ejercicio->az};
    float UnoDiagonal= ((UnoFilaUno[0]*UnoFilaDos[1]*UnoFilaTres[2])+(UnoFilaUno[1]*UnoFilaDos[2]*UnoFilaTres[3])+(UnoFilaUno[2]*UnoFilaDos[3]*UnoFilaTres[4])) - ((UnoFilaUno[4]*UnoFilaDos[3]*UnoFilaTres[2])+(UnoFilaUno[3]*UnoFilaDos[2]*UnoFilaTres[1])+(UnoFilaUno[2]*UnoFilaDos[1]*UnoFilaTres[0]));
    float DosFilaUno[5] = {Ejercicio->X,Ejercicio->Z,Ejercicio->R,Ejercicio->X,Ejercicio->Z};
    float DosFilaDos[5] = {Ejercicio->aX,Ejercicio->aZ,Ejercicio->aR,Ejercicio->aX,Ejercicio->aZ};
    float DosFilaTres[5] = {Ejercicio->ax,Ejercicio->az,Ejercicio->ar,Ejercicio->ax,Ejercicio->az};
    float DosDiagonal= ((DosFilaUno[0]*DosFilaDos[1]*DosFilaTres[2])+(DosFilaUno[1]*DosFilaDos[2]*DosFilaTres[3])+(DosFilaUno[2]*DosFilaDos[3]*DosFilaTres[4])) - ((DosFilaUno[4]*DosFilaDos[3]*DosFilaTres[2])+(DosFilaUno[3]*DosFilaDos[2]*DosFilaTres[1])+(DosFilaUno[2]*DosFilaDos[1]*DosFilaTres[0]));
    float TresFilaUno[5] = {Ejercicio->X,Ejercicio->Y,Ejercicio->R,Ejercicio->X,Ejercicio->Y};
    float TresFilaDos[5] = {Ejercicio->aX,Ejercicio->aY,Ejercicio->aR,Ejercicio->aX,Ejercicio->aY};
    float TresFilaTres[5] = {Ejercicio->ax,Ejercicio->ay,Ejercicio->ar,Ejercicio->ax,Ejercicio->ay};
    float TresDiagonal= ((TresFilaUno[0]*TresFilaDos[1]*TresFilaTres[2])+(TresFilaUno[1]*TresFilaDos[2]*TresFilaTres[3])+(TresFilaUno[2]*TresFilaDos[3]*TresFilaTres[4])) - ((TresFilaUno[4]*TresFilaDos[3]*TresFilaTres[2])+(TresFilaUno[3]*TresFilaDos[2]*TresFilaTres[1])+(TresFilaUno[2]*TresFilaDos[1]*TresFilaTres[0]));
    float CuatroFilaUno[5] = {Ejercicio->X,Ejercicio->Y,Ejercicio->Z,Ejercicio->X,Ejercicio->Y};
    float CuatroFilaDos[5] = {Ejercicio->aX,Ejercicio->aY,Ejercicio->aZ,Ejercicio->aX,Ejercicio->aY};
    float CuatroFilaTres[5] = {Ejercicio->ax,Ejercicio->ay,Ejercicio->az,Ejercicio->ax,Ejercicio->ay};
    float CuatroDiagonal= ((CuatroFilaUno[0]*CuatroFilaDos[1]*CuatroFilaTres[2])+(CuatroFilaUno[1]*CuatroFilaDos[2]*CuatroFilaTres[3])+(CuatroFilaUno[2]*CuatroFilaDos[3]*CuatroFilaTres[4])) - ((CuatroFilaUno[4]*CuatroFilaDos[3]*CuatroFilaTres[2])+(CuatroFilaUno[3]*CuatroFilaDos[2]*CuatroFilaTres[1])+(CuatroFilaUno[2]*CuatroFilaDos[1]*CuatroFilaTres[0]));
    float ResultadoUno = ((FilaUno[0]*UnoDiagonal)+(FilaUno[1]*DosDiagonal*-1)+(FilaUno[2]*TresDiagonal*1)+(FilaUno[3]*CuatroDiagonal*-1));
    cout<<"El Determinante W es: "<<ResultadoUno<<endl;
    Ejercicio->DetW=ResultadoUno;
    Imprimir(Ejercicio);
}
void Imprimir(C* Ejercicio){
    float resultado[5] = {Ejercicio->DetX, Ejercicio->DetY, Ejercicio->DetZ,Ejercicio->DetW,Ejercicio->DetSistema};
    cout << "el programa ha terminando de operar, los resultados fueron: " << endl;
    cout << "(" << (resultado[0]/resultado[4]) << "," << (resultado[1]/resultado[4]) << "," << (resultado[2]/resultado[4]) << "," << (resultado[3]/resultado[4]) << ")" << endl;
    cout << endl << endl;
}
//Termino
```
