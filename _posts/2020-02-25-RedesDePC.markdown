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

#### Codigos AES
> [Codigo-Java-AES](https://fluidattacks.com/web/defends/java/cifrar-simetricamente/)

#### Codigos RSA
> [Codigo-Rsa](https://www.devglan.com/java8/rsa-encryption-decryption-java)

> [Codigo-Rsa](https://mkyong.com/java/java-asymmetric-cryptography-example/)

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
