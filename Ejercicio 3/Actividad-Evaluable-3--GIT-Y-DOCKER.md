---
title: Actividad Evaluable 3- GIT Y DOCKER
author: Adrián Isidoro Álvarez
---

# Actividad Evaluable 3- GIT Y DOCKER

## Ejercicio 3 - Redes

### Despliegue de contenedores en red: Adminer y MariaDB

Creamos una red **bridge**:

```bash
docker network create --driver bridge redbd
```

Ahora creamos un contenedor con la imagen **mariadb** en la red creada anteriormente. El enunciado nos indica que debe ser accesible por el puerto **3306** y también nos especifica el usuario y contraseña. Por lo tanto el comando a utilizar será el siguiente:

```bash
docker run -d --network redbd --name bbdd --env MARIADB_ROOT_PASSWORD=root -p 3306:3306 -v /Documentos/git/DAWActividad3 mariadb:latest
```

Para ejecutar la imagen **Adminer** usamos este comando:

```bash
docker run --link bbdd:db -p 8080:8080 adminer
docker run -p 8080:8080 -e ADMINER_DEFAULT_SERVER=mysql adminer
```

Con esto ya podemos acceder a la base de datos a través de la interfaz web de **Adminer**:

![](/ejercicio3.assets/adminerbases.PNG)

Ahora creamos una base de datos y comprobamos desde la consola del servidor web que se ha creado con éxito:

![](/ejercicio3.assets/basededatosadminer.PNG)

![](/ejercicio3.assets/databaseconsole.PNG)

 

