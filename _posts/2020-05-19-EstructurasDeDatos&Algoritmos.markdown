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

