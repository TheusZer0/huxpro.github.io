---
layout: post
title: "Seminario de Programacion - TEL102"
subtitle: 'Seminario de Programacion - C++ - TEL102 - RamoUsm'
date: 2019-12-27 12:00:00
author: "TheusZero"
header-img: "images/post/c++.png"
catalog: true
tags:
  - Programacion
  - USM
  - C++
---

### Seminario de Programacion - TEL102

## Apuntes - Luego vienen los codigos uwu.

Arreglos: recordar definir que tipo de elemento sera nuestro arreglo, cada uno de los arreglos que tendra
el tipo entero, sera siempre un entero, por lo que hay que tener cuidado ( No es como en python que podias tener una lista con 3 tipos de elementos diferentes, como strings y enteros en una sola lista ) 
> recordar colocar el numero de arreglos que tendremos 

```vim
int arreglo [10]; //tendremos este arreglo con un total de 10 enteros
arreglo [7] = 3 ; // con esto decimos que en el puesto 7+1 este sera de un valor de 3
```

## Programas - TEL102

aqui pondre programas varios, tales como ejercicios de guias, proyectos o cosas asim
de manera que puedan quedar en la pag y sean faciles de buscar y ver.

#### Main

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

#### Ejercicios - Guia 

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

#### For - Basicos e Importantes

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

#### Entre Numeros (uso de if)

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

#### Raiz Cuadrada

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

## Controles

#### Control 1
```vim
/* 
 * DISCLAIMER: El siguiente archivo no contiene tildes a proposito, 
 * para evitar problemas de compatibilidad.
*/

#include<iostream>
#include<string>
#include<cmath>

struct vector{
	float *p;
	int dim;
};

// Funcion createVector: 20pts
vector createVector(){
	vector v;
	std::cout <<"Indique dimension del vector" << std::endl;
	std::cin >> v.dim;
	
	v.p = new float[v.dim];
	for(int i=0;i<v.dim;i++){
		std::cout<<"Ingrese dimension " << i + 1 << std::endl;
		std::cin >> v.p[i];
	}
	
	return v;
}

// Funcion sumVector: 20pts
vector sumVector(vector v1, vector v2){
	/* Determinar dimension mayor y crear vector 
	 * para almacenar resultado */
	int dim;
	if(v1.dim>v2.dim){
		dim = v1.dim;
	}else{
		dim = v2.dim;
	}
	vector v;
	v.dim = dim;
	v.p = new float[v.dim];
	
	/* Inicializar (puede ser como copia de un vector, 
	 * pero debe ser bien hecha!)*/
	for(int i=0;i<v.dim;i++){
		v.p[i] = 0;
	}
	
	// Sumar: 5pts
	for(int i=0;i<v1.dim;i++){
		v.p[i] += v1.p[i];
	}
	for(int i=0;i<v2.dim;i++){
		v.p[i] += v2.p[i];
	}
	
	return v;
}

// Funcion dotProductVector: 20pts
float dotProductVector(vector v1, vector v2){
	if(v1.dim == v2.dim){ // Verificacion de dimensiones (NO OBLIGATORIO) 
		// Crear variable que almacena resultado
		float res = 0;
		// Calculo producto punto
		for(int i=0; i<v1.dim; i++){
			res += v1.p[i]*v2.p[i];
		}
		return res;
	}else{
		std::cout << "Dimensiones incorrectas" << std::endl;
		return 0;
	}	
	
	
}

// Funcion normVector: 10pts
float normVector(vector v1){
	// Calculo norma
	return sqrt(dotProductVector(v1,v1));
}

// Funcion projectVector: 20pts
float projectVector(vector v1, vector v2){
	// Calculo de norma de proyeccion
	float proj = dotProductVector(v1,v2)/normVector(v2);
	return proj;
}


// Funcion unitaryVector: 10pts
vector unitaryVector(vector v1){
	// Calculo norma
	float norm = normVector(v1);
	vector v;
	v.dim = v1.dim;
	v.p = new float[v.dim];
	// Calculo vector unitario
	for(int i=0;i<v.dim;i++){
		v.p[i] = v1.p[i]/norm;
	}
	return v;
}
```

#### Control 2

```vim
/* 
 * DISCLAIMER: El siguiente archivo no contiene tildes a proposito, 
 * para evitar problemas de compatibilidad.
*/

#include<vector>
#include<cmath>
#include<iostream>

class PoligonoReg{
	public:
		PoligonoReg(){}
		PoligonoReg(int n, float l);
		virtual float getArea();
		virtual float getPerimetro();
		
	protected:
		int n_lados;
		float lado;
};

const float pi = 3.1415;


// PREGUNTA 1
// Pregunta 1.1: 15pts
PoligonoReg::PoligonoReg(int n, float l):n_lados(n),
lado(l){
}

float PoligonoReg::getArea(){
	float ap = (lado/2)/tan((2*pi/n_lados)/2);
	float area = n_lados*lado*ap*0.5;
	return area;
}

float PoligonoReg::getPerimetro(){
	return n_lados*lado;
}

// Pregunta 1.2: 15pts
// Ojo, esta es una posible solucion. Incluso solo la definicion de las
// clases era suficiente si se utilizaban las formulas correctas.
class Triangulo:public PoligonoReg{
	public:
		Triangulo(float l):PoligonoReg(3,l){}
};


class Cuadrado:public PoligonoReg{ 
	public:
		Cuadrado(float l):PoligonoReg(4,l){} 
};

// Pregunta 1.3: 20pts
std::vector<PoligonoReg> addCuadrado(std::vector<PoligonoReg> vecp, Cuadrado c){
	vecp.push_back(c);
	return vecp;
}

// PREGUNTA 2
// Pregunta 2.1: 10pts
class Envio{
	private:
		std::string direccion;
		bool Recibido;
	public:
		Envio(int Id, int Precio, std::string Direccion, bool Recibido);
		int Id;
		int Precio;
		void CambiaDireccion(std::string nuevaDireccion);
		void MarcarRecibido(bool Recibido);
	
};

// Pregunta 2.2: 20pts
Envio::Envio(int id, int precio, std::string Direccion, bool Recibido){
	this->Id=id;
	this->Precio=precio;
	this->direccion = Direccion; 
	this->Recibido=Recibido;
	
}

// Pregunta 2.3: 20pts
void Envio::CambiaDireccion(std::string nuevaDireccion){
	this->direccion= nuevaDireccion;

}

void Envio::MarcarRecibido(bool Recibido){
	this->Recibido=Recibido;
}