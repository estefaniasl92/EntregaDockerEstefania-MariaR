# Tarea Evaluable Docker



> Módulo Despliegue de Aplicaciones Web, realizado por María Rosete



[TOC]

## Ejercicio 1 - Servidor de base de datos



**Arrancar un contenedor que se llame web y que ejecute una instancia de una imagen con Apache y php.**

Descargar imagen:

```bash
$ docker pull php:7.4-apache
```

```bash
$ docker run -d --name web -p 8080:80 php:7.4-apache

```

![image-20240224020038601](Ejercicio1.assets/image-20240224020038601.png)



**Arrancar un contenedor que se llame bbdd y que ejecute una instancia de la imagen mariadb para que sea accesible desde el puerto 3306.**

Antes de arrancarlo visitar la página del contenedor en Docker Hub y establecer las variables de entorno necesarias para que:

* La contraseña de root sea root .
* Crear una base de datos automáticamente al arrancar que se llame prueba .
* Crear el usuario invitado con la contraseña invitado. 

Descargar imagen:

```bash
$ docker pullmariadb
```

```bash
$ docker run -d --name bbdd -p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=root \
-e MYSQL_DATABASE=prueba \
-e MYSQL_USER=invitado \
-e MYSQL_PASSWORD=invitado \
mariadb

```



![image-20240221181828213](Ejercicio1.assets/image-20240221181828213.png)



![image-20240221182719475](Ejercicio1.assets/image-20240221182719475.png)



Entregar un documento con las siguientes capturas de pantalla y los comandos empleados para resolver cada apartado:

- **Captura de pantalla y documento que desde el navegador muestre el fichero index.html .**

```bash
$ echo '<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Sitio Web</title>
</head>
<body>
    <h1>Bienvenido a Mi Sitio Web</h1>
    <p>Este es un sitio web de ejemplo creado con Docker, para el ejercicio 1</p>
</body>
</html>' > index.html

```



```bash
$ docker cp index.html 0ac9582d4557:/var/www/html
```

![image-20240224022408412](Ejercicio1.assets/image-20240224022408412.png)



![image-20240224022713543](Ejercicio1.assets/image-20240224022713543.png)



- **Captura de pantalla y documento que desde un navegador muestre la salida del script mes.php .**

```bash
$ echo '<?php' > mes.php
echo 'echo "Este es el mes actual: " . date("F");' >> mes.php
echo '?>' >> mes.php

```

```bash
$ docker cp mes.php 0ac9582d4557:/var/www/html

```

![image-20240224021500880](Ejercicio1.assets/image-20240224021500880.png)

![image-20240224021623714](Ejercicio1.assets/image-20240224021623714.png)





**Captura de pantalla y documento donde se vea el tamaño del contenedor web después de crear los dos ficheros.**

```bash
$ docker ps --size

```

![image-20240224022849648](Ejercicio1.assets/image-20240224022849648.png)

![image-20240224023015259](Ejercicio1.assets/image-20240224023015259.png)



**Captura de pantalla y documento donde desde un cliente de base de datos (instalado en tu ordenador) se pueda observar que hemos podido conectarnos al servidor de base de datos con el usuario creado y que se ha creado la base de datos prueba ( show databases ). El acceso se debe realizar desde el ordenador que tenéis instalado docker, no hay que acceder desde dentro del contenedor, es decir, no usar docker exec.**

Base de datos **dbeaver**:

![image-20240224001027867](Ejercicio1.assets/image-20240224001027867.png)

![image-20240224001116061](Ejercicio1.assets/image-20240224001116061.png)



![image-20240224000607209](Ejercicio1.assets/image-20240224000607209.png)





**Captura de pantalla y documento donde se comprueba que no se puede borrar la imagen mariadb mientras el contenedor bbdd está creado.**



```bash
$ docker ps -a
```

![image-20240224023846694](Ejercicio1.assets/image-20240224023846694.png)

```bash
$ docker rmi mariadb
```

![image-20240224023953080](Ejercicio1.assets/image-20240224023953080.png)





 