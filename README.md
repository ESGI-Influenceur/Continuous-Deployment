# Continuous-Deployment

<img src="https://electric-cloud.com/wp-content/uploads/use-case-graphic_continuous-delivery.png">


### Introduction 
Le Continuous Delivery, selon Martin Fowler, est une discipline du génie logiciel où vous construisez une application de telle manière qu'elle puisse être envoyée en production à tout moment. Cette façon de travailler de manière agile est très prisée par le mouvement DevOps dont la philosophie est : « You build it, you run it ».
### Technology Stack
Component         | Technology | Language
---               | ---        |  --- 
Projet            | [Symfony 4](https://symfony.com/4) | PHP
Build Tools| [Composer](https://getcomposer.org) | PHP
Artefact Packaging| [Docker](https://www.docker.com/) | ?
Continuous-Integration            | [Jenkins 2](https://jenkins.io) | JAVA
Continuous-Deployement            | [Xl Deploy](https://xebialabs.com/products/xl-deploy) | ?


### Build Symfony Project Image 
```
FROM composer:latest
# install all PHP dependencies
COPY . /app
RUN composer install


FROM php:7.2-apache
COPY --from=0 /app /var/www/html/
RUN apt-get update
RUN a2enmod rewrite
COPY ./000-default.conf /etc/apache2/sites-available/
EXPOSE 80
```

### Useful Links 
- devops : https://zestedesavoir.com/articles/88/la-methode-continuous-delivery/
- xldeploy : https://blog.xebialabs.com/2014/07/08/deploying-dockerized-application-xl-deploy/
