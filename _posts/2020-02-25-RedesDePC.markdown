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

## Links ricolinos

#### Drive con MUXO material
> [Drive hecho por mi UwU](https://drive.google.com/drive/u/0/folders/0AP6afRafbeuIUk9PVA)

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

> $ sudo apt-get install Wireshark 

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
>
## Tarea 2:



## Tarea 3:

#### Codigo Socket para servidor

Este codigo te abre un puerto a la escucha de manera infinita, es decir, si manda la respuesta el servidor seguira a la escucha a menos que este mismo programa sea cortado.

```vim
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

#### Codigo AES para encriptar un string

Este codigo genera una keysize de 168 para encriptar un string con el metodo AES y crea un archivo en la carpeta actual donde se encuentra ubicado el archivo.
El archivo que crea es el string encriptado, la keysize y la secretkey como tal de la siguiente forma

> StringEncripted,KeySize,SecretKey
 
```vim
package com.javapapers.java.security;
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
#### Codigo AES - retorna un archivo solo con la llave simetrica - (Este usare creo)
```vim
package com.javapapers.java.security;
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

#### Codigo RSA - Generar Llaves Privadas y Publicas

Este codigo sirve para crear un PATH=RSA/ que guarda los archivos de las llaves privadas y publicas

```vim
package com.devglan.rsa;

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

#### Codigo RSA - encriptar y desencriptar archivos - arreglado :D

```vim
package com.mkyong.asymmetric;
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

#### Encriptar Todo

#### Generar una llave simétrica AES

Aqui se genera un archivo "TareaRedes.txt" que corresponde a la encriptacion de un string a AES, como una llave simetrica.

> El archivo lleva de nombre:
>> TareaRedes.txt
>
>> Largo_Llave.txt

```vim
package com.javapapers.java.security;
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

#### Generar una llave privada RSA

Esto genera un directorio en la carpeta donde se ejecuta el programa, esta carpeta con el nombre de RSA guarda la llave secreta para el equipo

> RSA
>
>> privateKEY 

```vim
package com.devglan.rsa;
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
#### Encriptar la llave simétrica AES, utilizando la llave pública (disponible en Aula) del AlgoritmoRSA

Este codigo corresponde al ejercicio 2 de la tarea 3, ya que encripta la llave AES con la llave RSA publica y crea un archivo llamado RsaEncyption que corresponde a la llave AES encriptada con la llave publica AES

> El archivo lleva de nombre:
>> RsaEncyption

```vim
package com.mkyong.asymmetric;
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