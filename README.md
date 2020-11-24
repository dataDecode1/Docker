# Docker commands
- clear the stopped containers, volumes, images
   ```
   docker container prune
   docker volume prune
   docker image prune
   ```
- docker-compose making 2 differnet container talk to one another 
   - https://github.ibm.com/Krishna-Damarla1/Edeka/blob/master/ldap/docker-compose-persistent1.yml
   
- Pull or Import the docker image 
    - **docker pull cloudera/quickstart:latest** (sample Cloudera docker image installation)
          (or)
    - **docker import - cloudera/quickstart:latest < cloudera-quickstart-vm-5.13.0-0-beta-docker.tar.gz** (Import is better than pull. Download the package with download manager to surpass any pauses in bandwidths)
- Run the docker image
    - **docker run --hostname=quickstart.cloudera --privileged=true -t -it -p 8888:8888 -p 80:80 cloudera/quickstart /usr/bin/docker-quickstart**
- Show containers 
  - list only running containers - **docker ps**
  - Containers with assigned ports info - **docker container ls -a**
  - show only stopped Docker containers,  - **docker ps --filter "status=exited"** (or) **docker ps -f "status=exited"**
  - show all containers (those even exited) - **docker ps -a**
- Enter the existing docker container shell
    - docker exec -it container-id bash (or) docker exec -it container_id
- Start / stop containers
    - docker stop container_name
    - docker start container_name
    - docker restart container_name (give this command on running docker container)
- Kill the container 
  - **docker kill container_id**
  - kill all running containers - **docker ps -aq** 
  - Remove specific container - docker rm -f CONTAINER_ID
  - Remove all stopped containers - **docker rm $(docker ps -a -q)**  (or) **docker rm -f `` `docker ps -aq` ``**
- Display / Delete images 
  - **docker images**
  - Delete specific images - **docker image rm image_id1 image_id2**   
  - Delete all images - **docker rmi $(docker images -q)**
  - Incase image is used by stopped containers, force remove - **docker rmi -f <image_id>**
- Image build history
  - **docker image history --no-trunc image_name**

## Restore / Commit 
- [Restore last save point](https://stackoverflow.com/a/19616598/5757129)
    - **docker start container_id**
    - **docker attach container_id**
- [Commit after each run to preserve data](https://stackoverflow.com/a/19586345/5757129)
    - Display all containers -  **docker container ls -a**
    - **sudo docker commit <container_id> iman/ping**
    - **sudo docker run iman/ping ping www.google.com**

 ## Build and push image
  - **docker build -t <docker-hub-address/your-private-repo>/image-name:latest .**
  - **docker push <docker-hub-address/your-private-repo>/image-name:latest**

## Delete images / containers
- Delete the images -  docker rmi image_id Ex: docker rmi a3f949e5ebfd
- Delete the containers - docker stop container_id ; docker rm container_id Ex: docker rm a3f949e5ebfd
- Remove all those images at once that have exited container - **docker image prune -a** 
 
 Ref: https://docs.docker.com/engine/reference/commandline/image_prune/
      https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes
      
 ## Delete volumes / networks 
 
 docker system prune --volumes
 docker network rm network_id
 
 Ref: https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/

# Docker settings - UI - Preferences (Advanced)

- For some applications like cloudera quickstart,  Docker need 2 virtual cpus and minimum **8 gb ram**. Only then we can start all servers and cloudera manager sucessfully.
- Check system requirements like # of cpu, ram of your application before running docker image.

# Ref
- https://docs.docker.com/engine/reference/commandline/rm/
- https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/
- Cloudera docker installation https://www.youtube.com/watch?v=jILo-WnZUEY

# Others
-  Running Cloudera Quickstart has constraints of centos having outdated python in /usr/bin location. creating a seperate venv  is recommended / easier than updating python to newer versions in centos. (Some system files need the pre installed python version)
- Working with docker is easier than oracle virtual box. Copy paste between local m/c and docker dosenot need any specific folder sharing like in virtual box. Also, docker images can be build and pushed to any server easily than vm. 
 
# Virtual Box
- Use option + commnand to come out of virtual box environment. 
