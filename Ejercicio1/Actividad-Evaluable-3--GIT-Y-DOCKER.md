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

```
docker exec -it web bash
```

Una vez en la consola del contenedor, instalamos el editor nano utilizando los siguientes comandos:

```
apt-get update
apt-get install nano
```

Creamos nuestro fichero index.html y vemos el resultado desde el navegador:

![](ejercicio1.assets/index.PNG)

![](/ejercicio1.assets/Localhost8000.PNG)

