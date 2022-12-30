# dockerized symfony6 app

This is sample dockerized symfony app.


Dockerfile: 


 FROM php:8.1-apache

  RUN apt update && apt install -y \
      git \
      curl \
      zip \
      unzip

 # RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer 
   

  WORKDIR /var/www/html  
  COPY . .
  RUN chown -R www-data:www-data /var/www




----- X -----





#Building image

	docker build . -t dockerized_sysmfony6

#Running container

	docker run --name sysmfony6-app -p 8080:80 -d dockerized_symfony6

#On Browser

	http://localhost:8080
