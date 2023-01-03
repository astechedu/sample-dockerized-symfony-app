# dockerized symfony6 app

This is sample dockerized symfony app.


Dockerfile: 

<code>
 FROM php:8.1-apache
  RUN apt-get update && apt-get install -y \
      git \
      curl \
      zip \
      unzip
 #RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer  
  WORKDIR /var/www/html  
  COPY symfony6x ./symfony6x
  RUN chown -R www-data:www-data /var/www
</code>

:thumbsup:

#docker-compose.yml

<code>
version: "3"
services: 
  web:  
   build:    
    context: ./    
    dockerfile: Dockerfile       
   container_name: symfony6x   
   volumes:    
     - ./000-default.conf:/etc/apache2/sites-available/000-default.conf     
   ports:   
    - 8080:80
</code>

:thumbsup:

000-default.conf

<code>
<VirtualHost *:80>

ServerAdmin webmaster@localhost
DocumentRoot /var/www/html/public

ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>

#vim: syntax=apache ts=4 sw=4 sts=4 sr noet
</code>

:thumbsup:


#Building image

	docker build . -t dockerized_sysmfony6

#Running container

	docker run --name sysmfony6-app -p 8080:80 -d dockerized_symfony6

#On Browser

	http://localhost:8080




