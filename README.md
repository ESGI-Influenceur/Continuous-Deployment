# Continuous-Deployment
<p align="center">
  <img src="https://electric-cloud.com/wp-content/uploads/use-case-graphic_continuous-delivery.png">
</p>

### Introduction 
## CI/CD C’EST QUOI ?
Je ne vais pas vous refaire une définition mais voici ce que nous dit Wikipédia pour CI et CD :

CI : CONTINUOUS INTEGRATION
“L’intégration continue est un ensemble de pratiques utilisées en génie logiciel consistant à vérifier à chaque modification de code source que le résultat des modifications ne produit pas de régression dans l’application développée. […] Le principal but de cette pratique est de détecter les problèmes d’intégration au plus tôt lors du développement. De plus, elle permet d’automatiser l’exécution des suites de tests et de voir l’évolution du développement du logiciel.”

CD : CONTINUOUS DELIVERY
“La livraison continue est une approche d’ingénierie logicielle dans laquelle les équipes produisent des logiciels dans des cycles courts, ce qui permet de le mettre à disposition à n’importe quel moment. Le but est de construire, tester et diffuser un logiciel plus rapidement. L’approche aide à réduire le coût, le temps et les risques associés à la livraison de changement en adoptant une approche plus incrémentale des modifications en production. Un processus simple et répétable de déploiement est un élément clé.”


### Technology Stack
Component               | Technology                                              | Language
---                     | ---                                                     |  --- 
Projet                  | [Symfony 4](https://symfony.com/4)                      | PHP
Versionning             | [Github Entreprise](https://enterprise.github.com/home) | RUBY
Build Tools             | [Composer](https://getcomposer.org)                     | PHP
Artefact Packaging      | [DockerFile](https://www.docker.com/)                   | ?
Continuous-Integration  | [Jenkins 2](https://jenkins.io)                         | JAVA
Continuous-Deployement  | [Xl Deploy](https://xebialabs.com/products/xl-deploy)   | ?

### Environnements
Local | Intégration | Debug | Production
---   | ---         | ---   | ---

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

<p align="center" >
  <img src="https://static1.squarespace.com/static/588bb37b893fc0698d8db5f6/t/58b98f00e58c626106600bad/1488555778344/?format=1500w">
</p>

### Useful Links 
- devops : https://zestedesavoir.com/articles/88/la-methode-continuous-delivery/
- xldeploy : https://blog.xebialabs.com/2014/07/08/deploying-dockerized-application-xl-deploy/
- jenkins : https://getintodevops.com/blog/building-your-first-docker-image-with-jenkins-2-guide-for-developers
