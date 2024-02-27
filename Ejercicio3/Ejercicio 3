# Ejercicio 3 - Contenedores en red: Adminer y MariaDB

> Realizado por Estefanía Sastre Lois

[TOC]

## Creación de una red bridge "redbd".

```bash
$docker network create redbd
$docker network ls
```

![image-20240223092028772](./Ejercicio%203.assets/image-20240223092028772.png)

## Creación de un contenedor con una imagen de mariaDB.

La asociamos a la red "redbd" y al puerto 3306:

```bash
$docker run -d \
    --name mi_mariadb \
    --network redbd \
    -p 3306:3306 \
    -e MYSQL_ROOT_PASSWORD=contraseña \
    -v /ruta/a/directorio/local:/var/lib/mysql \
    mariadb
```

![image-20240223092256145](./Ejercicio%203.assets/image-20240223092256145.png)

## Creación de un contenedor Adminer.

Para conectarlo al contenedor de la BD:

```bash
$docker run -d \
    --name mi_adminer \
    --network redbd \
    -p 8080:8080 \
    adminer
```

![image-20240223092446576](./Ejercicio%203.assets/image-20240223092446576.png)

## Comprobación de que el contenedor Adminer puede conectar con mysql.

Para obtener la ip del contenedor:

```bash
$docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mi_mariadb
```

![image-20240223093349759](./Ejercicio%203.assets/image-20240223093349759.png)

![image-20240223101136774](./Ejercicio%203.assets/image-20240223101136774.png)

## Otras capturas

Lista de contenedores:

![image-20240223101309856](./Ejercicio%203.assets/image-20240223101309856.png)

Acceso a la BD desde la interfaz web de Adminer:

![image-20240223101335135](./Ejercicio%203.assets/image-20240223101335135.png)

Creación de una nueva base de datos:

![image-20240223101408472](./Ejercicio%203.assets/image-20240223101408472.png)

![image-20240223101418102](./Ejercicio%203.assets/image-20240223101418102.png)

Modo texto desde la consola para comprobar que se ha creado la BD:

```bash
$docker exec -it 87a2437335dc
$mariadb -u root -p
```

![image-20240223101619258](./Ejercicio%203.assets/image-20240223101619258.png)

Borrado de todos los contenedores, la red y los volúmenes:

```bash
$docker stop $(docker ps -aq)
$docker rm $(docker ps -aq)
$docker network rm redbd
$docker volume prune
```

![image-20240223102000365](./Ejercicio%203.assets/image-20240223102000365.png)