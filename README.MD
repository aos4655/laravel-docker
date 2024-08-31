# Proyecto Laravel con Docker

Este proyecto utiliza Docker para crear un entorno de desarrollo para una aplicación Laravel. A continuación, encontrarás instrucciones para instalar Laravel y levantar los contenedores necesarios. 

## Preparativos

Asegúrate de tener [Docker desktop](https://www.docker.com/products/docker-desktop/) y [Composer](https://getcomposer.org/) instalados en tu máquina. 

## Pasos de Instalación 

Lo primero que debes hacer es dirigirte a la carpeta docker donde se encuentran los archivos docker-compose.yml, Dockerfile y vhost.conf:

1. Abre una terminal en el directorio del proyecto.

2. Ejecuta los siguientes comandos:

    **Dirigirse a la carpeta con los archivos de configuracion de docker:**

   ```powershell
   cd docker

   **Para levantar los contenedores necesarios(apache, mysql y phpmyadmin):**

   ```powershell
   docker-compose up --build

3. Abrir una nueva terminal y ejecutar ahora estos comandos:

   ```powershell
   composer create-project laravel/laravel laravel-app

## Ejecucion de comandos en laravel

Tienes dos opciones:

1. Ejecutar el comando sobre el contenedor. Por ejemplo:

    ```powershell
   docker exec -it apache-laravel11-docker php artisan migrate:fresh

2. Abre una terminal en el directorio del proyecto.

    ```powershell
   docker exec -it apache-laravel11-docker bash
    #Se abrira directamente la consola de ese contenedor, ahi ya podrias ejecutar el comando directamente es decir: php artisan migrate:fresh 

## Ver el proyecto en el navegador

Al contenedor de apache ya le hemos indicado la ruta al index.php de laravel por lo que solo necesitas desde docker desktop clicar sobre donde pone los puertos y ya se te abrira en el navegador.  

## Utilizar el contenedor de mysql para la base de datos de Laravel

Como bien sabras, laravel11 trae consigo por defecto como base de datos sqlite. Pero para poder cambiarla a mysql, deberemos mopdificar el archivo .env y copiar esta configuracion:

    ```powershell
   DB_CONNECTION=mysql
   DB_HOST=mysql
   DB_PORT=3306
   DB_DATABASE=laravel
   DB_USERNAME=miusuario
   DB_PASSWORD=mipassword