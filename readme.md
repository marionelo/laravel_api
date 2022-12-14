# Proyecto Laravel

Este proyecto esta hecho con docker, PHP (Laravel), MySQL y NGINX, a continuación se muestran las configuraciones previas:

### Copiando el .env

```sh
# copy env to run all general project
$ cp .env.example .env
```

Para poder indicar puertos de nginx, base de datos con su password, existe un .env en el cual se puede configurar

```sh
# variables to our new proojects, these variables will be used 
# by docker compose
PROJECT_NAME=nombre_del_proyecto

HTTP_PORT=puerto_para_http
SSL_PORT=puerto_para_https

DB_PORT_EXT=puerto_para_mysql(33061)
DB_ROOT_PASS=password_para_user_root_mysql
DB_NAME=name_to_our_database
```

### Ejecutando el proyecto

```sh
# run docker project
$ docker-compose up --build -d

# Ejecutar para ver que los 3 servicios esten corriendo
$ docker ps 
```

### Correr composer install

```sh
$ docker compose exec -ti php bash

# Una vez dentro ejecutar los siguientes comandos

$ composer install && \
cp .env.example .env && \
chmod -R 777 storage && \
chmod -R 777 bootstrap
```

### Revisando el resultado

Para poder ver el resultado final, hay que verlo en el navegador con el puerto que fue asignado dentro del .env en HTTP_PORT, por ejemplo si asignamos HTTP_PORT=8080, revisaremos con la siguiente url

```sh
    http://localhost:puerto_para_http
```


### Migraciones dentro de laravel

```sh
$ php artisan migrate --seed
```
