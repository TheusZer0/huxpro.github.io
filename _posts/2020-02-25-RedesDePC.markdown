---
layout: post
title: "Redes de Computadoras - 2019"
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
---

# Redes de Computadoras - 2do Semestre 2019 - Rudy Malonnek

## Links ricolinos
Codigo-Java-AES(https://fluidattacks.com/web/defends/java/cifrar-simetricamente/)

## Tarea 3:

#### Codigo Socket para servidor

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
