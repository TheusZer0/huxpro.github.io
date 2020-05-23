---
layout: post
title: "Estructura de Datos y Algoritmos"
subtitle: 'EDA - 2020-1 - Vourkas'
date: 2020-03-29 12:00:00
author: "TheusZero"
header-img: "images/post/EDA/portada.png"
catalog: true
comments: true
tags:
  - Programacion
  - USM
  - C
  - Tareas
---

# Estructura de Datos y Algoritmos con Vourkas

## Apuntes

#### punteros
> **Funcionamiento basico de punteros**

```Python
int main()
{
    int a=8; //Declaración de variable entera de tipo entero
    int *puntero; //Declaración de variable puntero de tipo entero
    puntero = &a; //Asignación de la dirección memoria de a

    printf("El valor de a es: %d. \nEl valor de *puntero es: %d. \n",a,*puntero);
    printf("La dirección de memoria de *puntero es: %p",puntero);

    return 0;
}
```
#### printf
> printf("%c",var) te imprime el indice
> printf("%s",var) te imprime desde ese indice en adelante

## Main simple
```Python
//
// Created by TheusZero
//

#include <stdio.h>
#include <math.h>
#include <stdlib.h>

int main() {
    return 0;
}
```
## Ejercicios en C (sin punteros ;-))

No los hice todos, solo los que pense que eran importantes.

#### imprimirSumaPares
```Python
    void imprimirSumaPares(){
        int numero = 100;
        for (int i = 0; i <= numero ; ++i) {
            if (i%2 == 0){
                printf("the numer is %d \n",i);
            }
        }
    }
```
#### leerNumeroDel_cien_al_uno
```Python
void leerNumeroDel_cien_al_uno(){
    /* */
    int cien = 100;
    int arreglo[100];
    int arregloInvertido[100];
    for (int i = 0; i <= cien ; ++i) /*se crea un array con numeros del 1 al cien*/ {
        arreglo[i] = i+1;
    }
    for (int k = 0; k < cien; ++k) /*se crea un array que ingresa los numeros del anterior array pero invertidos*/ {
        arregloInvertido[k] = arreglo[cien-(k+1)];
    }
    for (int j = 0; j < cien ; ++j) /*se imprime el recorrido de uno de los array*/ {
        printf("elemento %d del array es %d\n ",j,arregloInvertido[j]);
    }
}
```
#### ayudantiaUno_Ejercicio_Reloj
```Python
 int Hora,Minuto;
    float Angulo;
    printf("ingrese la hora: \n");
    scanf("%i",&Hora);
    printf("ingrese los minutos: \n");
    scanf("%i",&Minuto);
    Angulo = (30*Hora)+Minuto*(-5.5);
    printf("el angulo es %f",Angulo);
}
```
#### Algoritmo de strings

> lo saque de internet jiji despues ideare una forma de hacerlo sin punteros. **(Recordatorio)**

```Python
// C program to print all permutations with duplicates allowed
#include <stdio.h>
#include <string.h>

/* Function to swap values at two pointers */
void swap(char* x, char* y)
{
    char temp;
    temp = *x;
    *x = *y;
    *y = temp;
}

/* Function to print permutations of string
   This function takes three parameters:
   1. String
   2. Starting index of the string
   3. Ending index of the string. */
void permute(char* a, int l, int r)
{
    int i;
    if (l == r)
        printf("%s\n", a);
    else {
        for (i = l; i <= r; i++) {
            swap((a + l), (a + i));
            permute(a, l + 1, r);
            swap((a + l), (a + i)); // backtrack
        }
    }
}

/* Driver program to test above functions */
int main()
{
    char str[] = "AB";
    int n = strlen(str);
    permute(str, 0, n - 1);
    return 0;
}

```
#### encontrarValor_Minimo
```Python
int encontrarValor_Minimo(){
    int arreglo[7] = {3,4,5,6,7,1,2};
    int contador = 0;
    for (int i = 0; i < arreglo[i] ; ++i) {
        if ((arreglo[i]) > (contador)) {
            contador = arreglo[i];
        };
    }
    printf("%d",contador);
    return 0;
}
```

## Ejercicios en C (con punteros ;-))

#### contador de vocales y consonantes
```Python
//
// Created by TheusZero on 5/20/2020.
//

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <string.h>

void getConsonatsVowel(char* x){
    int recorrido = 0;
    int vocal = 0;
    int consonante =0;
    recorrido = strlen(x); // se calcula automatico el total de caracteres de la frase
    for (int i = 0; i < recorrido; ++i) { //for para recorrer el puntero
        if (((x[i]) == 'a') || ((x[i]) == 'e') || ((x[i]) == 'i') || ((x[i]) == 'o') || ((x[i]) == 'u')){//if simple
            vocal  += 1;
        } else {
            consonante += 1;
        }
    }
    printf("Las vocales son %d\n",vocal);
    printf("Las consonantes son %d\n",consonante);
}

int main() {
    char *frase[50];
    scanf("%s",frase);
    getConsonatsVowel(frase);
    return 0;
}
```

#### leer archivos y triangulos rectangulos

```Python
//
// Created by TheusZero on 5/22/2020.
//
#include <string.h>
#include <stdlib.h>
#include <stdio.h>

#define MAXCHAR 1000
int main() {
    int largo = 0;
    int base = 0;
    char Base = ' ';
    FILE *fp;
    char str[MAXCHAR];
    char* filename = "E:\\DiscoHDD_Progra\\EDA\\test.txt";

    fp = fopen(filename, "r");
    if (fp == NULL){
        printf("Could not open file %s",filename);
        return 1;
    }
    while (fgets(str, MAXCHAR, fp) != NULL) {//funciona como un for que itera sobre cada una de las lineas del archivo, es un code importante.
        largo += 1; //se obtiene el largo
    }
    base = strlen(str); // aqui obtengo la base
    fclose(fp);
    return 0;
}
```
