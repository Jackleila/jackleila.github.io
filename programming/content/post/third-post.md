---
title: "Useful docker commands to always have nearby"
date: 2021-09-22T21:37:34+02:00
draft: false
---

Just a list of docker commands I use pretty often.

### General commands

Show running containers:

	docker ps
	
Show all containers:

	docker ps -a
	
	
Information about a docker:
	
	docker inspect CONT
	
Open bash in docker:

	docker exec -it /bin/bash CONT
	
Delete container:

	docker rm CONT
	
List images:
	
	docker images
	
Remove image:

	docker image rm IMG
	
Build image:

	docker build --target production-stage -t NAME_IMG DOCKERFILE_DIR
	
Run image 

	docker run -p 8080 --name CONT_NAME IMG_NAME

### Docker compose


	docker-compose up
	
	docker-compose down
	
Option `-d` so it won't show logs on screen
	