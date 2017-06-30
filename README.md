# Sylius on Docker Compose

Run Sylius e-commerce platform (based on Symfony 3) with Docker Compose.

## New Sylius Project
To create a new Sylius project just run the following:

```
wget http://getcomposer.org/composer.phar
php composer.phar create-project -s beta sylius/sylius-standard sylius
cd sylius
git clone https://github.com/elliotjreed/sylius-docker-compose.git docker
cd docker
docker-compose up -d
```

You can then run the necessary `sylius:install` and `yarn` commands to initialise your Sylius install by running the following:

`docker-compose exec php initialise-sylius`

When prompted, the following settings should be entered:

Database Host: mysql
Database Port: 3306
Database Username: sylius
Database Password: sylius
Database Name: sylius_dev

You then access the container with:

`docker-compose exec php`

Note: you'll be in the Sylius root directory (_/var/www/html_) by default;

You can get the IP address of the Sylius Docker container using the following:

`docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' php`
