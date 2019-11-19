# Docker Setup for Laravel 6

This is a simple [Docker](https://www.docker.com/) setup to run a local [Laravel](https://laravel.com/) development environment.

**Included:**

- [Nginx](https://www.nginx.com/) 1.17
- [PHP](https://www.php.net) 7.3 FPM
- [MariaDB](https://mariadb.org/) 10.4
- [Redis](https://redis.io/) 5.0

## Installation

1. Install [Docker](https://www.docker.com/).
1. Clone this [repository](https://github.com/noreading/docker-for-laravel).
   ```bash
   git clone git@github.com:noreading/docker-for-wordpress.git
   ```
1. Remove the `.git` folder:
   ```bash
   rm -rf .git
   ```
1. Edit the file `docker/nginx/site.conf` and add the wanted local domain
   (e.g. dev.my-laravel-app.com).
1. Add the domain to your local `hosts` file.
1. Build the docker containers.
   ```bash
   docker-compose build
   ```
1. Start the containers (as a daemon).
   ```bash
   docker-compose up -d
   ```
1. Login to the PHP container.
   ```bash
   docker-compose exec php bash
   ```
1. Install composer.
   ```bash
   php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
   ```
   ```bash
   php composer-setup.php
   ```
   ```bash
   php -r "unlink('composer-setup.php');"
   ```
   ```bash
   mv composer.phar /usr/local/bin/composer
   ```   
1. Create a new laravel project.
   ```bash
   composer create-project --prefer-dist laravel/laravel html
   ```
1. Overwrite the .env file.
   ```bash
   mv .env html/.env
   ```

## Basic docker-compose commands

1. Start the containers:
   ```bash
   docker-compose up -d
   ```
1. Stopping the containers:
   ```bash
   docker-compose stop
   ```
1. Restarting the containers:
   ```bash
   docker-compose restart
   ```
1. Deleting the containers:
   ```bash
   docker-compose rm
   ```
1. Logging in by SSH into a container:
   ```bash
   docker-compose exec {container name} bash
   ```
