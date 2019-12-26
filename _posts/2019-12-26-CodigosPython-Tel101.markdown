---
layout: post
title: "Codigos Python - Tel101"
subtitle: 'CodigosPython - Tel101 - OpenSource - Iniciacion a la programacion'
date: 2019-12-26 12:00:00
author: "TheusZero"
header-img: "images/post/python.png"
tags:
  - Shell
  - Programacion
  - Python
  - USM
---

### Codigos Python - Tel101 "OpenSource"

Estos fueron los programas que hice para el ramo "Iniciacion a la programacion", fueron sacados de todos lados, algunos estan hechos por mi y hay otros que no.
Sin embargo los publico aqui como una forma de promover la educacion y la programacion.
Estos codigos fueron hechos para TEL101. Pero sirven para cualquier ramo que contenga python. EJ: "IWI"


### Libro de Programacion - "Apuntes de programacion"
>> Este es un OpenSource hecho para que podamos avanzar en programacion, segun el libro de "Apuntes de programacion", el codigo es libre y cada uno puede entrar, configurarlo y mejorarlo para que cada uno de nosotros podamos aprender más y mejorar en python...

>> Capitulo 21,22,23

```vim
def Saludo(nombre):
    try:
        print("Hola,",nombre)
    except:
        print("Los valores ingresados no son correctos")
def Circulos(radio):
    from math import pi
    Perimetro = 2*pi*radio
    Area = pi*(radio**2)
    print("Perimetro: ",Perimetro)
    print("Area: ",Area)
def Promedio(n1,n2,n3,n4):
    promedio = (n1+n2+n3+n4)/4
    print(promedio)
def Centimetros_a_Pulgadas(centimetros):
    Pulgada = float(2.54)
    print(centimetros/Pulgada,"in")
def Numero_Inverso(numero):
    NuevoNumero = str(numero)
    print(NuevoNumero[::-1])
def HorasFuturas(HoraActual,NumeroDeHoras):
    print("por terminar")
def ParteDecimal(real):
    entero = int(real)
    print(entero-real)
#NOMBRE = input("ingrese su nombre: ")
#Saludo(NOMBRE)
#Radio_Circulo = int(input("Ingrese el radio del circulo"))
#Circulos(Radio_Circulo)
#Promedio(int(input("Ingrese su primera nota:")),int(input("Ingrese su segunda nota: ")),int(input("Ingrese su tercera nota: ")),int(input("Ingrese su cuarta nota: ")))
#Centimetros_a_Pulgadas(int(input("Ingrese longitud:")))
#Numero_Inverso(int(input("ingrese un numero de 3 digitos: ")))
#PORTERMINAR!!!!!!!!!!: HorasFuturas(input("ingrese su hora actual: "), input("ingrese la cartidad de horas: "))
#ParteDecimal(float(input("ingrese un numero real")))
def Año_Bisiesto(año):#aqui empieza el capitulo 22
    print("no esta terminado")
def PalabraMasLarga(PalabraUno,PalabraDos):
    LargoPalabraUno = len(PalabraUno)
    LargoPalabraDos = len(PalabraDos)
    if LargoPalabraUno>LargoPalabraDos:
        print("La palabra uno", PalabraUno,"tiene",(LargoPalabraUno-LargoPalabraDos),"letra mas que la palabra",PalabraDos)
    elif LargoPalabraDos>LargoPalabraUno:
        print("La palabra dos", PalabraDos, "tiene", (LargoPalabraDos-LargoPalabraUno),"letras mas que la palabra",PalabraUno)
    else:
        print("las palabaras tienen el mismo largo")
def Ordenamiento(NumeroUno,NumeroDos):
    if NumeroUno>NumeroDos:
        print(NumeroDos,NumeroUno)
    elif NumeroUno<NumeroDos:
        print(NumeroUno,NumeroDos)
    else:
        print("son iguales")
def Edad(Dia,Mes,Año):
    from datetime import date
    from time   import localtime
    FechaDeNacimiento = date(Año,Mes,Dia)
    F = localtime()
    AñoHoy=F.tm_year
    MesHoy=F.tm_mon
    DiaHoy = F.tm_mday
    Hoy= date(AñoHoy,MesHoy,DiaHoy)
    Hoy_Menos_Fecha = (Hoy-FechaDeNacimiento).days
    Años = int(Hoy_Menos_Fecha/365)
    print(Años)
#Año_Bisiesto(int(input("ingrese un año a evaluar: ")))
#PalabraMasLarga((input("Ingrese una palabra")),(input("Ingrese su segunda palabra: ")))
#Ordenamiento(int(input("Ingrese un numero")),int(input("Ingrese otro numero")))
#print("Ingrese su fecha de nacimiento") & Edad(int(input("dias")),int(input("mes")),int(input("años")))
def Multiplos(Numero): #AQUI EMPIEZA EL CAPITULO 23
    Hasta = 11
    for x in range(1,Hasta):
        print (Numero,"x",x,"=",Numero*x)
def PotenciasDos(Numero):
    for x in range (Numero+1):
        print(2**x)
def Divisores(Numero):
    for x in range(1,Numero+1):
        if (Numero%x == 0):
            print(x)
def TablaMultiplicar():
    lista = []
    listados = []
    listatres = []
    for x in range (1,11):
        lista.append(x)
    for i in range(11,21):
        listados.append(i)
    print(lista)
    print(listados)

    #de que otra forma se puede hacer?, NO COMPLETADO
#Multiplos(9)
#PotenciasDos(int(input("ingrese un numero: ")))
#Divisores(int(input("ingrese numero: ")))
#TablaMultiplicar() NO COMPLETADO
def ExpresionesConConjuntos():
    a = {5,2,3,9,4}
    b = {3,1}
    c = {7,5,5,1,8,6}
    d = {6,2,4,5,5,3,1,3,7,8}
    e ={(2,3),(3,4),(4,5)}
    f = [{2,3},{3,4},{4,5}]

    print(len(c))
    print(len(set(d)))
    print(a&(b|c))
    print((a&b)|c)
    print(c-a)
    print(max(e))
    print(f[0]<a)
    print(set(range(4))&a)
    len(set("perro"))
    len({"perro"})
#ExpresionesConConjuntos()
def Contar_Letras(oracion):
#es un ejercicio bonito para empezar con diccionarios, creo que es la base para lo siguiente y la verdad me dejo con una duda...
#COMO ELIMINO LOS ESPACIOS DE UNA LISTA? ##for iterado y le chantas un if x != " ": ...
    Oracion = oracion.lower()
    diccionario = dict()
    for x in Oracion:
        if x not in diccionario and x != ' ':
            diccionario[x] = 1
        elif x == ' ':
            print("El programa no cuenta los espacios")
        else:
            diccionario[x] +=1
    print(diccionario)
#Contar_Letras("El elefante avanza hacia Asia")
def Contar_Vocales(oracion):
    Oracion = oracion.lower()
    diccionario = {"a":0,"e":0,"i":0,"o":0,"u":0 }
    for x in Oracion:
        if x in diccionario:
            diccionario[x] += 1
    print(diccionario)
#Contar_Vocales("El elefante avanza hacia Asia")
def Contar_Iniciales(oracion):
    Oracion = oracion.lower()
    Lista = Oracion.split()
    Diccionario = dict()

    for x in range (len(Lista)):
        for y in Lista[x][0]:
            if y not in Diccionario:
                Diccionario[y] = 1
            else:
                Diccionario[y] += 1
    print(Diccionario)
#Contar_Iniciales("El elefante avanza hacia Asia")
def Obtener_largo_palabras(oracion):
    Lista = oracion.split()
    Diccionario = dict()
    for x in Lista:
        if x not in Diccionario:
            Diccionario[x] = len(x)
        else:
            print("Hay algunas palabras repetidas tales como:  ", x)
    print(Diccionario)
#obtener_largo_palabras('el gato y el pato son amigos')
def Contar_Palabras(oracion):
    Oracion = oracion.lower()
    Lista = Oracion.split()
    Diccionario = dict()
    for x in Lista:
        if x not in Diccionario:
            Diccionario[x] = 1
        else:
            Diccionario[x] += 1
    print(Diccionario)
#Contar_Palabras("El sobre esta sobre el pupitre")
def Palabras_repetidas(oracion):
    Oracion = oracion.lower()
    Lista = Oracion.split()
    Lista_Dos = []
    Diccionario = dict()
    for x in Lista:
        if x not in Diccionario:
            Diccionario[x] = 1
        else:
            Diccionario[x] +=1
    for y in Diccionario:
        if Diccionario[y] != 1:
            Lista_Dos.append(y)
    print(Lista_Dos)
#palabras_repetidas('El partido termino cero a cero')
#palabras_repetidas('El sobre esta sobre el mueble')
#palabras_repetidas('Ay, ahi no hay pan')
def Hay_llaves_pares(Dict):
    Lista = []
    for x in Dict:
        if x%2 == 0:
            Lista.append("True")
        else:
            Lista.append("False")
    for y in Lista:
        if y == "True":
            print("True")
            break
        else:
            print(False)
            break
def Hay_valores_pares(Dict):
    Lista = []
    for x in Dict.values():
        if x%2 == 0:
            Lista.append("True")
        else:
            Lista.append("False")
    for y in Lista:
        if y == "True":
            print("True")
            break
        else:
            print(False)
            break
#d1 = {1: 2, 3: 5}
#d2 = {2: 1, 6: 7}
#hay_llaves_pares(d1)
#hay_llaves_pares(d2)
#hay_valores_pares(d1)
#hay_valores_pares(d2)
def Maximo_par(Dict):
#    for x in Dict.keys(),Dict.values():
    contador = []
    for key in Dict:
        contador.append(key + Dict[key])
    new = sorted(contador)
    ultimo = new[::-1]
    print(ultimo[0])
#d = {5: 1, 4: 7, 9: 0, 2: 2}
#Maximo_par(d)
```
