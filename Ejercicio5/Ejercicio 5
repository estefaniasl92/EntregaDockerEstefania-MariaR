# Ejercicio 5 - imagen con Dockerfile - Aplicación web



> Módulo Despliegue de Aplicaciones Web, tarea realizada  por María Rosete 



[TOC]

## **Creación inicial del contenedor** - documenta los pasos hasta el borrado del mismo



Para la realización de este ejercicio es necesario tener una cuenta en Docker Hub.

- **Arranca un contenedor que ejecute una instancia de la imagen php:7.4-apache , que se llame web y que sea accesible desde un navegador en el puerto 8000.**

  Lo llamo **sitioweb** para diferenciarlo del anterior creado:

```bash
$ docker run -d --name sitioweb -p 8000:80 php:7.4-apache
```

![image-20240225151621366](Ejercicio%205.assets/image-20240225151621366.png)



- **Coloca en el directorio raíz del servicio web ( /var/www/html ) un sitio web donde figure el nombre de los componentes del grupo el sitio deberá tener al menos un archivo index.html y un archivo .css**

```bash
$ docker cp index.html sitioweb:/var/www/html
$ docker cp estilo.css sitioweb:/var/www/html
$ docker cp docker.png sitioweb:/var/www/html

```

![image-20240225154955290](Ejercicio%205.assets/image-20240225154955290.png)

![image-20240225154457330](Ejercicio%205.assets/image-20240225154457330.png)



- **Coloca en ese mismo directorio raíz un archivo llamado mes.php que muestre el nombre del mes actual. Ver la salida del script en el navegador**

  ```bash
  $ nano mes.php
  ```

```bash
$ <?php
echo "Este es el mes actual: " . date("F");
?>

```

```bash
$ docker cp mes.php sitioweb:/var/www/html

```

![image-20240225155121706](Ejercicio%205.assets/image-20240225155121706.png)

![image-20240225155147629](Ejercicio%205.assets/image-20240225155147629.png)

- **Borrar el contenedor**

```bash
$ docker rm sitioweb

```

![image-20240225160331740](Ejercicio%205.assets/image-20240225160331740.png)

## **Bloque de código con el Dockerfile**

- **Automatizar estas operaciones creando un fichero Dockerfile**

```bash
$ nano Dockerfile
```

![image-20240225160814373](Ejercicio%205.assets/image-20240225160814373.png)

## Captura de pantalla y documento donde se vea el comando que crea la nueva imagen



```bash
$ docker build -t imagenweb .

```

![image-20240225161223595](Ejercicio%205.assets/image-20240225161223595.png)



## Captura de pantalla y documento donde **se vea la imagen subida a tu cuenta de Docker Hub**.

- **Subir la imagen a la cuenta de Docker Hub**

```bash
$ docker login

```

Etiquetar la imagen:

```bash
$ docker tag imagenweb marla960/dockerestefaniamariarosete:web

```

Subir imagen:

```bash
$ docker push marla960/dockerestefaniamariarosete:web

```

![image-20240225162712255](Ejercicio%205.assets/image-20240225162712255.png)

![image-20240225162925452](Ejercicio%205.assets/image-20240225162925452.png)



## Captura de pantalla y documento donde **se vea la bajada de la imagen por parte de otra persona del grupo y la creación de un contenedor**.



```bash
$ docker pull marla960/dockerestefaniamariarosete:web

```

![image-20240226101919064](Ejercicio%205.assets/image-20240226101919064.png)

```bash
$ docker run -d --name webestefania -p 8000:80 marla960/dockerestefaniamariarosete:web
```

![image-20240226102340058](Ejercicio%205.assets/image-20240226102340058.png)

![image-20240226102519420](Ejercicio%205.assets/image-20240226102519420.png)



## Captura de pantalla y documento donde **se ve el acceso al navegador con el sitio servido**.

Descargar la imagen: 

```bash
$ docker pull marla960/dockerestefaniamariarosete:web

```

![image-20240225164332134](Ejercicio%205.assets/image-20240225164332134.png)

Ejecutar un contenedor basado en la imagen:

```bash
$ docker run -d --name sitioweb -p 8000:80 marla960/dockerestefaniamariarosete:web

```

![image-20240225164757710](Ejercicio%205.assets/image-20240225164757710.png)

![image-20240225164844236](Ejercicio%205.assets/image-20240225164844236.png)

