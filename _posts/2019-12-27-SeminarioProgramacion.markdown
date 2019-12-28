---
layout: post
title: "Seminario de Programacion - TEL102"
subtitle: 'Seminario de Programacion - C++ - TEL102 - RamoUsm'
date: 2019-12-27 12:00:00
author: "TheusZero"
header-img: "images/post/c++.png"
tags:
  - Programacion
  - USM
  - C++
---

### Seminario de Programacion - TEL102

### Apuntes - Luego vienen los codigos uwu.

Arreglos: recordar definir que tipo de elemento sera nuestro arreglo, cada uno de los arreglos que tendra
el tipo entero, sera siempre un entero, por lo que hay que tener cuidado ( No es como en python que podias tener una lista con 3 tipos de elementos diferentes, como strings y enteros en una sola lista ) 
> recordar colocar el numero de arreglos que tendremos 

```vim
int arreglo [10]; //tendremos este arreglo con un total de 10 enteros
arreglo [7] = 3 ; // con esto decimos que en el puesto 7+1 este sera de un valor de 3
```

### Programas - TEL102

aqui pondre programas varios, tales como ejercicios de guias, proyectos o cosas asim
de manera que puedan quedar en la pag y sean faciles de buscar y ver.

### Main

```vim
//
// Created by TheusZero on 27-12-2019.
//

#include <iostream>
#include <string>
using namespace std;

int main() {
    cout << "Libreria estandar, ocupar para todos los programas" << " ## Recordar ##" ;
    return 0;
}
```

### Ejercicios - Guia 

```vim
#include <iostream>
#include <string>

using namespace std;

int main ()
{
	int i;
	cout << "Ingresa el primer valor numerico: ";
	cin >> i;
	cout << "Su valor ingresado fue = " << i;

	int NumeroDos;
	cout << ".\n" << "Ingresa el segundo valor: ";
	cin >> NumeroDos;
	cout << "El valor que ingreso fue = " << NumeroDos;

	cout << ".\n" << "Este programa calculara la suma de los valores entregados";
	cout << ".\n";
	cout << "La suma de sus valores es: " << i+NumeroDos;
}
```

```vim
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string Nombre;
	cout << "Ingrese su nombre = " << ".\n";
	cin >> Nombre;
	cout << "Su nombre es " << Nombre;
	cout << ".\n";
	cout << "Hola " << Nombre;
}
```

```vim
#include <iostream>
#include <string>
#include <stdio.h>
using namespace std;
int main()
{
	int Numero;
	float Flotante;
	cout << "Ingrese el numero que quiere convertir a flotante: ";
	cin >> Numero;
	cout << "\n";
	Flotante = float(Numero);
	cout << "Su numero es: " << "\n";
	cout << Flotante << "\n";
}
```

### For - Basicos e Importantes

```vim
//
// Created by TheusZero on 27-12-2019.
//

#include <iostream>
#include <string>

using namespace std;

int ForEntero(int numero) {
    int x = 100;
    int y = 1;
    if ( numero < y){
        cout << "el numero ingresado no corresponde";
    }
    else {
        for (int i = numero ; i < x ; ++i) {
            cout << i << "\n";
        }
    }
    return 0;
}

int ForPalabra(string palabra){
    for (int i = 0; i < palabra.length(); ++i) {
        cout << palabra[i] << "\n";
    }
    return 0;
}

int main(){
/*    
    int numeroEntero;
    cin >> numeroEntero;
    ForEntero(numeroEntero);
*/
    string Palabra;
    cin >> Palabra;
    ForPalabra(Palabra);
}
```

### Entre Numeros (uso de if)

```vim
//
// Created by TheusZero on 27-12-2019.
//

#include <iostream>
#include <string>

using namespace std;

int main() {
    int x = 1;
    int y = 10;
    int numero;
    cin >> numero;
    if (numero <= 10 && numero >=1 ){ //el and aqui en c++ es un &&
        printf("Su numero cumple uwu.\n");
    }
    else{
        printf("su numero no cumple.\n");
    }
    return 0;
}
```

### Raiz Cuadrada

```vim
//
// Created by theuszero on 10/6/19.
//

#include <iostream>
#include <string>
#include <math.h>

using namespace std;

int main() {
    double numeroUno;
    cout << "Este programa calcula la raiz cuadrada de un numero " << "porfavor, ingrese su numero: " ;
    cin >> numeroUno;
    cout << "su numero elegido fue: "<< numeroUno;
    cout << "\n";
    cout << "  la raiz cuadrada de su numero es: " << sqrt(numeroUno) ;
    return 0;
//    double c = 9.0;
//    double result;
//    result = sqrt(c);
//    std:cout<<result;
//    return 0;
}
```