# Tarea Entregable - Docker



> Módulo Despliegue de Aplicaciones Web , tarea realizada por María Rosete



[TOC]

# Ejercicio 4 - Docker Compose

**Desplegar la aplicación cmatrix utilizando docker-compose.**



**Entregar las siguientes capturas de pantalla y los comandos empleados para resolver el ejercicio:**

Crear archivo **docker-compose.yaml:** 

```bash
$ nano docker-compose.yaml
```

```bash
version: '3'
services:
  cmatrix:
    image: ubuntu:latest
    container_name: cmatrix_container
    tty: true
    command: /bin/bash -c "apt-get update && apt-get install -y cmatrix && cmatrix"

```



- **Captura de pantalla y documento donde se vea el fichero docker-compose.yaml .**

![image-20240224102818754](Ejercicio%204.assets/image-20240224102818754.png)

Crear contenedor:

```bash
$ docker-compose up -d

```

![image-20240224102930058](Ejercicio%204.assets/image-20240224102930058.png)



- **Captura de pantalla y documento donde se vea la aplicación funcionando. Se valorará conseguir el efecto Greenrain .**

  ```bash
  $ docker ps 
  $ docker exec -it cmatrix_container /bin/bash
  $ cmatrix
  
  ```

  ![image-20240224103502962](Ejercicio%204.assets/image-20240224103502962.png)

  ![Captura desde 2024-02-23 10-17-24](./assets/Captura%20desde%202024-02-23%2010-17-24.png)

  Puedes cambiar el color:

  green, red, blue, white, yellow, cyan, magenta and black

```bash
$ cmatrix -C magenta -f

```

![image-20240224104249710](Ejercicio%204.assets/image-20240224104249710.png)

Cambiar la velocidad:

```bash
$ cmatrix -u 2
```



- **Explicar brevemente cómo funciona esta aplicación.**

  La aplicación **cmatrix** es un programa que simula el famoso efecto  "Matrix" que se ve en la película del mismo nombre. Funciona generando  una animación de caracteres que caen de arriba hacia abajo en la  pantalla de la terminal, creando la ilusión de un flujo de datos similar al que se ve en la película.

  Crea una cuadrícula de caracteres que representan los caracteres que  caen y los actualiza en la pantalla en cada fotograma. Puedes  personalizar varios aspectos de la animación, como el color de los  caracteres, la velocidad de caída y el tipo de fuente utilizada.

