# MariaDB & PHP Adminer container

Quick setup MariaDB server ([MySQL fork](https://en.wikipedia.org/wiki/MariaDB)) with super simple 
PHP browser management.

## Installation

1. Clone repository into some folder

	`git clone -branch mariadb git@github.com:justcoded/docker-library.git ./`
	
2. Create .env file from the example

	`cp .env.example .env`
	
3. If you need a specific version of MariaDB, please edit .env file `MARIADB_VER` variable (for example you can set `10.4` instead of `latest`)*.

_* Note: If you updated .env file you need to stop and recreate your container._ 

## Running

Run `docker-compose up -d` to launch container as a daemon (you need to be inside the folder you cloned a repository).

To stop docker container run `docker-compose stop`.

All databases and mysql data will be placed under `data` and `logs` folder.

In case you have problems try to stop your container and then recreate it with `docker-compose up -d --force-recreate`.

### Server access

To access your MySQL server use such credentials (from HeidiSQL or SequelPRO):

	Host: localhost
	Port: 33306
	User: root
	Password: developer

From another Docker container **on MacOS**:

	Host: host.docker.internal 

From another Docker container **on Linux**:

	Host: 172.17.0.1

To access Adminer:

	URL: http://localhost:33380/
	Host: mariadb
	User: root
    Password: developer

### Environement variables

Except MariaDB version, you can set different external ports for MariaDB and Adminer with `.env` file.
And if you don't like Adminer theme - you can also set a different one (check and [official site](https://www.adminer.org) the the themes list)
 

## MySQL server config

By default it configured to low memory usage. In case you need advanced configuration you can edit `my.cnf` file, which is used as a main config file when you start a server.
