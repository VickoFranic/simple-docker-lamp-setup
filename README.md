# Simple Docker LAMP setup

- PHP 7.2
- mysql 5.7

## How to use it

Main purpose of this Docker LAMP setup is to quicky give you a simple working development environment.

Steps:
1. copy `.docker-config` folder and `.docker-compose.yml` file to the root of your project.

2. run `docker-compose up -d`

3. open up [http://localhost:8000](http://localhost:8000)

---

## web container

web container is based on official PHP Docker image with apache.

There are official helper scripts `docker-php-ext-configure`, `docker-php-ext-install`, and `docker-php-ext-enable` which enable you to more easily install additional PHP extensions.
Check the [Dockerfile](.docker-config/web/Dockerfile) for example usage.

Container will run on port `8000` on localhost.
Container will also have `composer` globally installed.

## db container

db container is based on official MySQL Docker image.

There is a custom [SQL script](.docker-config/db/init.sql) which will run on container init and create new empty database, if database doesn't exist already. You can add your custom SQL code here, if necessary.

## adminer container

adminer container is based on official Adminer Docker image.  
> Adminer is a quick & easy tool for database management from web browser.

Adminer will run on: [http://localhost:8080](http://localhost:8080)

Default values for database login:
```
Server: db
Username: root
Password: root
Database: db
```