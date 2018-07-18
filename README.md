# Docker commands 

## Show running contaners
  - docker ps 
  
## Show all containers even exited 
  - Docker ps -a
  
## Remove specific container 
  - docker rm -f CONTAINER_ID
  
## Remove all containers
docker rm -f `docker ps -aq`

## To docker shell
  - docker run -it image_name sh
  - docker exec -it <container>
  
## Image build history
  - docker image history --no-trunc image_name 
  
## Delete all images
  - docker rmi $(docker images -q)

## Build image
  - docker build -t <docker-hub-address/your-private-repo>/image-name:latest .

## Push image
  - docker push <docker-hub-address/your-private-repo>/image-name:latest
