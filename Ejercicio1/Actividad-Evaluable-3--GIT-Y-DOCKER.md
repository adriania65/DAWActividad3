---
title: Actividad Evaluable 3- GIT Y DOCKER
author: Adrián Isidoro Álvarez
---

# Actividad Evaluable 3- GIT Y DOCKER

## Ejercicio 1 - Trabajo con Imágenes

### Servidor web

Arrancamos un contenedor que ejecute una instancia de la imagen `php:7.4-apache `, al que llamamos `web` y hacemos que se pueda acceder al mismo desde el puerto 8000 de nuestro navegador.

Para ello ejecutamos el siguiente comando:

```bash
docker run -it -p 8000:80 --name web -v /adriania/Ejercicio1:/var/www/html/ -d php:7.4-apache
```

Nos conectamos a la consola del contenedor de docker con el comando:

```bash
docker exec -it web bash
```

Una vez en la consola del contenedor, instalamos el editor nano utilizando los siguientes comandos:

```bash
apt-get update
apt-get install nano
```

Creamos nuestro fichero `index.html` y vemos el resultado desde el navegador:

![](/ejercicio1.assets/index.PNG)

![](/ejercicio1.assets/Localhost8000.PNG)

Ahora creamos el fichero php `mes.php` que nos indique el mes actual en nuestro navegador, para ello simplemente creamos el fichero al igual que el `index.html` y comprobamos que funciona correctamente:

![](/ejercicio1.assets/mes.PNG)

![](/ejercicio1.assets/localhostmes.PNG)

Aquí podemos ver el tamaño del contenedor `web` después de haber creado ambos ficheros:

![](/ejercicio1.assets/sizedocker.PNG)

Para finalizar tenemos que parar el contenedor y posteriormente borrarlo de la siguiente forma:

```bash
docker stop web
docker rm web
```

### Servidor de base de datos

Para este apartado usaremos un contenedor para ejecutar la imagen `mariadb`.

Para ello solamente tenemos que descargar esta imagen y lanzarla introduciendo los datos del enunciado:

```bash
docker pull mariadb
docker run --detach --name bdd --env MARIADB_USER=invitado --env MARIADB_PASSWORD=invitado --env MARIADB_ROOT_PASSWORD=root --env MARIADB_DATABASE=prueba mariadb:latest
```

Nos conectaremos de la misma forma que en el apartado anterior y comprobamos que podemos conectarnos a la base de datos utilizando el usuario que hemos creado anteriormente:

![](/ejercicio1.assets/mariadb.PNG)

Una vez aquí utilizamos el siguiente comando para ver las bases de datos existentes:

```
show databases;
```

![](/ejercicio1.assets/databaseprueba.PNG)

Ahora intentaremos borrar nuestro la imagen `mariadb` sin antes parar el contedor `bdd` para comprobar que no está permitido:

![](/ejercicio1.assets/errorborrar.PNG)

Por último eliminamos el contenedor `bdd` parándolo anteriormente con los comandos `stop` y `rm`:

![](/ejercicio1.assets/sincontenedores.PNG)