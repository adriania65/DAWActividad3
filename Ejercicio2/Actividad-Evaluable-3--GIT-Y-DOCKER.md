---
title: Actividad Evaluable 3- GIT Y DOCKER
author: Adrián Isidoro Álvarez
---

# Actividad Evaluable 3- GIT Y DOCKER

## Ejercicio 2 - Almacenamiento

### Bind mount para compartir datos

Crearemos un directorio **saludo** con el comando `mkdir`, y en su interior creamos un fichero **index.html** y lo editamos con `nano`:

![](/ejercicio2.assets/index.PNG)

Arrancamos dos contenedores basados en la imagen php:7.4-apache haciendo un bind mount de la carpeta saludo en la carpeta /var/www/html de cada contenedor. Utilizaremos los puertos que nos indica el enunciado y sus nombres serán c1 y c2:

```bash
sudo docker container run --name c1 -v /Documentos/git/DAWActividad3/saludo:/var/www/html --publis 8181:80 --detach --restart=always php:7.4-apache
```

Accedemos a nuestro fichero mediante el navegador utilizando el puerto **8181**.

![](/ejercicio2.assets/localhost8181.PNG)

Realizamos el mismo proceso para el segundo contenedor y comprobamos que editando el fichero **index.html** podemos acceder y ver los cambios:

![](/ejercicio2.assets/indexmodificado.PNG)

![](/ejercicio2.assets/localhost8282.PNG)

Por último se nos pide demostrar que se puede acceder a la vez a ambos contenedores:

![](/ejercicio2.assets/entrarc1yc2.PNG)

