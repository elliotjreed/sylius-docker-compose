# Sylius on Docker Compose

Run Sylius e-commerce platform (based on Symfony 3) with Docker Compose.

`wget http://getcomposer.org/composer.phar`
`php composer.phar create-project -s beta sylius/sylius-standard sylius`

`cd sylius`
`git clone https://github.com/elliotjreed/sylius-docker-compose.git docker`

`cd docker`
`docker-compose up -d`

If you do not already have a Sylius project installed you can run the following to get everything set up and ready to go:

`docker-compose exec php initialise-sylius`
