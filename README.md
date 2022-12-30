# dockerized symfony6 app

This is sample dockerized symfony app.

#Building image

	docker build . -t dockerized_sysmfony6

#Running container

	docker run --name sysmfony6-app -p 8080:80 -d dockerized_symfony6
