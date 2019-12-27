---
layout: post
title: "Codigos Python - Tel101"
subtitle: 'CodigosPython - Tel101 - OpenSource - Iniciacion a la programacion'
date: 2019-12-26 12:00:00
author: "TheusZero"
header-img: "images/post/python.png"
tags:
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

### Apuntes y Captura de Numeros

```vim
# while True:
# try:
# x = int(input("ingrese un numero: "))
# break

# except ValueError:
# print("No ingreso un entero valido. Intentelo denuevo")

# except: #generico, recibe todo, tipo de else en los try
# print("Otra excepcion..")

# en un solo bloque se puede encerrar lso tipos de errores, tipo como una tupla
# la palabra raise crea tu propia excepcion y la lanza, crea el error

# CACAError = NameError

# try:
# raise CACAError("Hola!!",5) #CREA UNA EXCEPCION
# except CACAError as e: #RECUPERA ESA EXCEPCION
# print(type(e))
# print(e.args)
# print(e.args[0])
# print(e.args[1])
# print(e)
# raise #llama al error, sale error ya que no esta definido como tal

# archivos = ["hola.txt","chao.txt"]
# for arg in archivos:
# try:
# f = open(arg, "r") #el programa llega ahasta aqui, una vez el programa funciona salta al else,
# ya que no se crea ningun tipo de error y el else, opera leyendo las lineas del .txt
# except IOError:
# print("No se puede abrir ", arg)
# else:
# print(arg, " tiene ", len(f.readlines()),"lineas.")
# f.close()
# finally: #el finaññy va al ultimo y SIEMPRE SIEMPRE se ejecuta
# print("tuvo weno el pleaños")

def CapturaNumeros(n):
    try:
        int(n)

    except:
        print("n no es entero")
        return  # sale de la funcion

    lista = []
    contador = 0

    for elemento in range(n + 1):  # si n es 5 entonces tomara 4 veces los valores

        lista.append(float(input("añada sus numeros: ")))

    return lista  # sale de la funcion con la lista
```

### Ayudantía 10-04

```vim
def BuscaVocales (lista):
    consonantes = "qwrtypsdfghjkl ñzxcvbnm"
    lista2 = []
    for p in lista:
        for l in p:
          if l not in consonantes:
             lista2.append(l)
    return lista2

def BuscaConsonantes (lista):
    consonantes="qwrtypsdfghjklñzxcvbnm"
    lista2 = []
    for p in lista:
        for l in p:
          if l in consonantes:
             lista2.append(l)
    return lista2

def BuscaLetras (lista):
    letras = "qwrtypsdfghjklñzxcvbnmaeiou"
    lista2 = []
    for p in lista:
       for l in p:
          if l in letras:
             lista2.append(l)
    return lista2

a=input("Inserte las palabras a analizar : ")
lista = []

lista.append(a)
b=a.split(" ")

print(BuscaLetras(lista))
nletras=BuscaLetras(lista)
print("La cantidad de letras es: " + str(len(nletras)))

print(BuscaVocales(lista))
nvocales=BuscaVocales(lista)
print("La cantidad de vocales es: " + str(len(nvocales)))

print(b)
print("La cantidad de palabras son: "+ str(len(b)))

print(BuscaConsonantes(lista))
nconsonantes=BuscaConsonantes(lista)
print("La cantidad de consonantes es: " + str(len(nconsonantes)))
```

### Contador de Numeros y DivideListas

```vim
def CapturaNumeros(n):
    while True:
        try:
            Entero = int(n)
            lista = []
            for i in range(0, Entero):
                S = input("ingrese un numero:")
                lista.append(S)
            print(lista)
            return lista
        except:
            print("ingrese valores validos")
            continue

def DivideListas(Lista1,Lista2):
    try:
        NuevaLista = []
        NuevaLista2 = []
        ListaAux = []
        ListaFinal =[]

        #CAMBIO DE LISTA, SE PUEDE QUITAR SIN PROBLEMAS
        if len(Lista1) < len(Lista2):
            ListaAux = Lista1
            Lista1 = Lista2
            Lista2 = ListaAux

        #TRABAJAR CON INT = CONVERTIR A INT
#        for item in Lista1:
#            NuevaLista.append(int(item))
#        for itemDos in Lista2:
#            NuevaLista2.append(int(itemDos))

        #OPERAR CON FLOAT DE UNA
        for item in Lista1:
            NuevaLista.append(float(item))
        for itemDos in Lista2:
            NuevaLista2.append(float(itemDos))

        #forma uno
    #    for elemento in Lista1:
    #        print(elemento)
    #        for elemento2 in Lista2:
    #            ListaFinal.append(float(elemento/elemento2))

        #forma dos
        for elemento in range (len(Lista1)):
            if NuevaLista[elemento]/NuevaLista2[elemento]:
                ListaFinal.append((float(NuevaLista[elemento]/NuevaLista2[elemento])))
            else:
                print("0")
    except IndexError:
        print(ListaFinal)


print("Menu")

try:
    N1= int(input("ingrese un entero numero 1: "))
    N2= int(input("ingrese un entero numero 2: "))
    A = CapturaNumeros(N1)
    B = CapturaNumeros(N2)
    DivideListas(A,B)

except ValueError:
    print("el numero ingresado no fue un entero, por lo tanto, se cerrará el programa")
```

### Cambia Vocales

```vim
def CambiaVocal(oracion, vocal):
    vocales = ["a","e","i","o","u",]
    palabra=""
    print(len(oracion))
    range(len(oracion))
    print()
    for i in range(len(oracion)):
        print(i, oracion[i])
        if oracion[i] in vocales:
            palabra+=vocal
        else:
            palabra+=oracion[i]
    return palabra

oracion=input("Ingrese la oración: ")
vocal=input("Ingrese la vocal por la que se cambiaran todas las vocales: ")
print(CambiaVocal(oracion,vocal))
```

### Cancionero (Base de Datos mini uwu)

```vim
def AgregarArtista(datos, artista):
    datos.append(artista)
    datos.append([])
def AgregarAlbum(cancionero,artista,album):
    for indice in range(len(cancionero)):
        if cancionero[indice] == artista:
            cancionero[indice + 1].append(album)
            cancionero[indice + 1].append([])
def AgregarCancion(cancionero,artista,album,cancion):
    for indice in range(len(cancionero)):
        if cancionero[indice] == artista:
            for indiceDos in range (len(cancionero[indice+1])):
                if cancionero[indice+1][indiceDos] == album:
                    cancionero[indice+1][indiceDos+1].append(cancion)

def DiscosArtistas(cancionero,artista):
    for indice in range (len(cancionero)):
        if cancionero[indice] == artista:
            print("El artista que desea conocer es:")
            print(artista)

            for indice2 in range (0,len(cancionero[indice+1]),2):
                print("El nombre de su/s album/s es/son: ")
                print(cancionero[indice+1][indice2])
                for c in cancionero[indice + 1][indice2+1]:
                    print("su/s cancion/nes es/son: ")
                    print(c)





cancionero =[]

AgregarArtista(cancionero,"Lucho Jara")
AgregarArtista(cancionero, "Muse")
AgregarArtista(cancionero, "Robbie Williams")

AgregarAlbum(cancionero,"Lucho Jara","Para que no me olvides")
AgregarAlbum(cancionero,"Robbie Williams", "Feel")
AgregarAlbum(cancionero,"Muse","Skip")

AgregarCancion(cancionero,"Lucho Jara","Para que no me olvides", "Sin Retorno")
AgregarCancion(cancionero,"Robbie Williams","Feel", "Rock Dj")

while True:

    QueArtista = input("que artista desea conocer o saber su discografía:  ")
    DiscosArtistas(cancionero,QueArtista)

    print(cancionero)
    
```

### Control 3

```vim
def dividirListas(ListaUno,ListaDos):
    #Hecho con ayuda de david tapia en ayudantia y completado anteriormente en casa

    try:

        DigitoUno=0
        DigitoDos=1
        ListaFinal = []
        ListaAux = []

        if len(ListaUno) < len(ListaDos):
                ListaAux = ListaUno
                ListaUno = ListaDos
                ListaDos = ListaAux

        while True:
            ListaFinal.append(float(ListaUno[DigitoUno]/ListaDos[DigitoDos]))
            print(ListaFinal)
            DigitoUno+=1
            DigitoDos+=1

            if DigitoUno == len(ListaUno):
                return ListaFinal

            if DigitoDos == len(ListaDos):
                DigitoDos=0
    except ValueError:
        print("en la lista se encuentra un string o un caracter invalido")
    except TypeError:
        print("no coloco una lista, es decir, el int no esta en una lista")
    except IndexError:
        print("el numero es negativo, no se hara la operacion")
    except NameError:
        print("la variable ingresada no es valida")

def sonAmigos(NumeroUno,NumeroDos):

    try:

        Lista1 = []
        Lista2 = []
        ListaSuma =[]
        ListaSuma2 =[]
        VariableUno = 0
        VariableDos = 0
        for x in range (1,NumeroUno):
            Lista1.append(x)
            if NumeroUno%x == 0:
                ListaSuma.append(x)

        for i in range (1,NumeroDos):
            Lista2.append(i)
            if NumeroDos%i == 0:
                ListaSuma2.append(i)

        for z in range (len(ListaSuma)):
            VariableUno += ListaSuma[z]

        for w in range (len(ListaSuma2)):
            VariableDos += ListaSuma2[w]

        if (VariableUno == NumeroDos) and (VariableDos == NumeroUno):
            print("Si son numeros Amigos")
            return True
        else:
            print("no es numero amigo")
            return False

    except TypeError:
        print("ingresó un numero invalido, un caracter o un string")
    except IndexError:
        print("se ingreso un indice invalido, no sirve")
    except NameError:
        print("la variable ingresada no es valida")


while True:
    try:
        print("menu")
        print("Opcion 1 : sonAmigos")
        print("Opcion 2 : dividirListas")
        print("Opcion 3 : salir")

        Opcion = int(input("ingrese la opcion"))

        if Opcion == 1:
            sonAmigos(int(input("ingrese un numero 1"),int(input("ingrese un numero 1"))))
        if Opcion == 3:
            break

    except ValueError:
        print("ingrese una opcion valida")
```

### Captura de Strings

```vim
Lista = ["a","s","c","d",2,34,45,6,7,834,5]
for x in range(len(Lista)):
    try:
        int(Lista[x])
    except ValueError:
        print(Lista[x])
```

### Contador de Vocales y Palabras

```vim
x=1
def estadisticasString (x):
    x = list(input("Ingresar palabra:"))
    contador_vocales = 0
    contador_palabras = 0
    contador_letras = 0
    contador_espacios = 0
    for i in (x):
        if i == 'a' or 'e' or 'i' or 'o' or 'u':
            contador_vocales +=1
            vocales=contador_vocales

        if i==' ':
            contador_espacios +=1
        if i in (x):
            contador_letras +=1
            y=((contador_letras) - (contador_espacios))

    print("Vocales=", vocales)
    print("Letras=", y)
    
estadisticasString(x)
estadisticasString("frase")
```
### Ensayo?? - No se que wea

```vim
#def esNumeroPerfecto(Numero):
#    try:
#        NumeroNuevo = int(Numero)
#        Lista = []
#        Contador = 0

#        if numero < 0:
#            raise Exception

#        for Numeros in range (1,NumeroNuevo):
#            Lista.append(Numeros)
#        for NumerosDos in range (1,len(Lista)+1):
#            if NumeroNuevo%NumerosDos == 0:
#                Contador += NumerosDos
#            if Contador == NumeroNuevo:
#                print("si se suman los numeros que cumplen la propiedad da como resultado", Contador)
#                return True
#        if not Contador == NumeroNuevo:
#            print("El numero no es perfecto")
#            return False
#    except ValueError:
#        print("debe ingresar un dato valido, es decir un numero, no un string")

#    except Exception:
#        print("Ingrese Un Numero Positivo")
#        return ""
#        break

#Numero = input("ingrese el numero que desea calcular: ")
#esNumeroPerfecto(Numero)



#forma david tapia (modificada)
#def sumarListas(Lista1,Lista2):
#    ListaFinal = []
#    for i in range (len(Lista1)):
#        if (i == (len(Lista1))):
#            ListaFinal.append(Lista1[i]+Lista2[i+1])
#        else:
#            ListaFinal.append(Lista1[i]+ Lista2[i-2])
#    return ListaFinal
#    print(ListaFinal)

#def sumarListas(Lista,ListaDos):
#    ListaFinal = []
#    for x in range (len(Lista)):
#      if x in range (len(Lista)):
#        Lista[x] += ListaDos[x-2]
#        ListaFinal.append(Lista)
#    print(ListaFinal)

#Lista = [2,3,4,5]
#ListaDos = [6,7,8]

#sumarListas(Lista,ListaDos)

#mi forma 1
    #print(i)
    #for x in range (len(Lista2)):
        #print(x)
        #Lista1[i] += Lista2[x]
#ListaFinal.append(Lista1)
#Lista1[0] += Lista2[1]
#Lista1[1] += Lista2[2]
#Lista1[2] += Lista2[0]
#Lista1[3] += Lista2[1]
#print(ListaFinal)

#Lista = [2,3,4,5]
#ListaDos = [6,7,8]

#sumarListas(Lista,ListaDos)




#def sumarListasDos(ListaUno,ListaDos):

#    ListaFinal = []
#    ListaUno.append(ListaDos)
#    ListaFinal.append(ListaUno)
#    print(ListaFinal)

#    for i in range (len(ListaFinal[0])):
#        print(i)



#sumarListasDos(Lista,ListaDos)
```

### Ensayo Listo? - toy todo perdido haciendo este blog uwu

>> Recodatorio mental: elegir nombres mas originales y que descibran mucho
 
```vim
def dividirListas(ListaUno,ListaDos):
    try:
        print(ListaUno)
        print(ListaDos)

        DigitoUno=0
        DigitoDos=1
        ListaFinal = []
        ListaAux = []

        if len(ListaUno) < len(ListaDos):
                ListaAux = ListaUno
                ListaUno = ListaDos
                ListaDos = ListaAux

        while True:
            ListaFinal.append(float(ListaUno[DigitoUno]/ListaDos[DigitoDos]))
            print(ListaFinal)
            DigitoUno+=1
            DigitoDos+=1

            if DigitoUno == len(ListaUno):
                return ListaFinal

            if DigitoDos == len(ListaDos):
                DigitoDos=0
    except ValueError:
        print("en la lista se encuentra un string o un caracter invalido")
    except TypeError:
        print("no coloco una lista, es decir, el int no esta en una lista")
    except IndexError:
        print("el numero es negativo, no se hara la operacion")

def sonAmigos(NumeroUno,NumeroDos):

    try:

        Lista1 = []
        Lista2 = []
        ListaSuma =[]
        ListaSuma2 =[]
        VariableUno = 0
        VariableDos = 0
        for x in range (1,NumeroUno):
            Lista1.append(x)
            if NumeroUno%x == 0:
                ListaSuma.append(x)

        for i in range (1,NumeroDos):
            Lista2.append(i)
            if NumeroDos%i == 0:
                ListaSuma2.append(i)

        for z in range (len(ListaSuma)):
            VariableUno += ListaSuma[z]

        for w in range (len(ListaSuma2)):
            VariableDos += ListaSuma2[w]

        if (VariableUno == NumeroDos) and (VariableDos == NumeroUno):
            print("Si son numeros Amigos")
            return True
        else:
            print("no es numero amigo")
            return False

    except TypeError:
        print("ingresó un numero invalido, un caracter o un string")

sonAmigos(17296,18416)
sonAmigos(1184,1210)
dividirListas([2,3,4,5],[6,7,8])
```

### Fibonacci Pares
```vim
nterms = int(input("ingrese cuantos numeros quiere de la sucecion de fibonacci: "))

try:
    n1 = 0
    n2 = 1
    count = 0
    lista = []
    listapares = []

    if nterms <= 0:
       print("Ingrese un numero positivo")
    elif nterms == 1:
       print("Fibonacci sequence upto",nterms,":")
    else:
       print("Fibonacci sequence upto",nterms,":")
       while count < nterms:
           nth = n1 + n2
           n1 = n2
           n2 = nth
           count += 1
           lista.append(n1)

    for i in range(len(lista)):
        if lista[i]%2 == 0:
            listapares.append([lista[i]])



    print(lista)
    print(listapares)


except ValueError:
    print("ingrese un numero valido, no un strg o caracteres")
```

### Iva 

```vim
#MENU

Opcion = 1

print("Menu")
print("Opcion 0 = Agregar una Factura")
print("Opcion 1 = Facturas Emitidas al total")
print("Opcion 2 = Facturas recibidas del total")
print("Opcion 3 = SALIR")
print("Opcion -1 = se imprimirá el resultado actual y se cerrará el programa")
print("Opcion -2 = se imprimira el resultado actual y se empezara desde 0")

FacturasEmitidas = 0
FacturasRecibidas = 0
ValorDeFactura = 0
CantidadDeFacturas = 0
Opcion = 1

while (Opcion == 0) or (Opcion == 1) or (Opcion == 2) or (Opcion == 3) or (Opcion == -1) or (Opcion == -2):

    IVA = int(ValorDeFactura * 0.19)
    Opcion = int(input("Selecione una opcion del menu"))

    if Opcion == -2:
        print(ValorDeFactura)
        ValorDeFactura = 0
        continue

    elif Opcion == 0:
        ValorDeFactura += int(input("Ingrese un Valor de factura"))
        CantidadDeFacturas += 1
        print(ValorDeFactura)

    elif Opcion == 1:
        FacturasEmitidas = (ValorDeFactura-IVA)
        ValorDeFactura -= IVA
        print(FacturasEmitidas)

    elif Opcion == 2:
        FacturasRecibidas = (ValorDeFactura+IVA)
        ValorDeFactura += IVA
        print(FacturasRecibidas)

    elif Opcion == 3:
        print("saliendo...")
        break

    elif Opcion == -1:
        print(ValorDeFactura)
        break

    else:
        print("Vuelve a intentarlo ")
```
