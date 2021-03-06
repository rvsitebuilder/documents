# Installation for Windows 10

- [Install on Local Web Server](#install-on-local-web-server)
- [Server Requirement](#server-requirement)
- [Install step](#install-step)
- [Install on Docker](#install-on-docker)
  - [Install Docker](#install-docker)
  - [Install step](#install-step-1)

## Install on Local Web Server

### Server Requirement

Same as Laravel, https://laravel.com/docs/5.8/installation#server-requirements.

### Install step

1. Download file https://raw.githubusercontent.com/rvsitebuilder/docker-lamp-php72/master/public/index.php and copy to web document root
2. Open browser http://<local_ip>:8080

If you don’t have any web server locally, follow these steps.

## Install on Docker

### Install Docker

[Install Docker for Windows](https://docs.docker.com/v17.09/docker-for-windows/install/)

### Install step

1. Download and Extract https://github.com/rvsitebuilder/docker-lamp-php72/archive/master.zip
2. update docker .env file

```
Optional to change WEBSERVER_PORT,LOCALE,TZ
```

3. run docker build and up

```
cd docker-lamp-php72

docker-compose -f docker-compose.yml up --build -d

docker-compose -f docker-compose.yml up -d
```

4. After that you will got dev environment like below (local ip coule be like 192.168.x.x) :

```php
   http://<local_ip>:8080 for document root
   http://<local_ip>:8082 for phpMyAdmin

   document root path:
       <workspacke_path>/docker-lamp-php72/public/
   app path:
       <workspacke_path>/docker-lamp-php72/app/

   db access info:
      MARIADB_HOST = mariadb
      MARIADB_DATABASE = dbname
      MARIADB_USER = dbuser
      MARIADB_PASSWORD = dbpass
```

5. Open browser http://<local_ip>:8080

```
admin user: admin@admin.com
admin pass: 123456
```
