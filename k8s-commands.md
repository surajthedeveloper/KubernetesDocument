Docker Commands
===============

docker --version
docker login 															=> Login with username and password

docker images
docker image rm <IMAGE_ID>
docker image history <IMAGE_ID>

docker search <IMAGE_NAME>
docker pull <IMAGE_NAME>												=> If image doesnot exist in local it will pull from Docker Server

docker run <IMAGE_NAME>
docker run -p [actual-port]:[container-port] <IMAGE_NAME> 				=> Binding port
docker run -d -p [local-port]:[docker-port] <IMAGE_NAME> 			    => Deattach mode 
docker run -d -p [local-port]:[docker-port] --restart=always <IMAGE_NAME> 			    
																		=> On restart of docker the container will be restared if --restart=always is mentioned

docker logs <LOG_ID>													=> For Logs
docker logs -f <LOG_ID> 												=> For tailing logs

docker container
docker container ls			= docker ps
docker container ls -a
docker container rm <CONTAINER_ID>										=> To remove container
docker container prune -f 												=> To remove stopped containers forcefully
docker container kill <CONTAINER_ID>			=> Immidiate termination of process (SIGTERM) 
docker container stop <CONTAINER_ID>			=> Graceful shutdown of process(SIGKILL)
docker container pause <CONTAINER_ID>
docker container unpause <CONTAINER_ID>
docker container restart <CONTAINER_ID>
docker container inspect <CONTAINER_ID>									=> To inspect about the container


docker events															=> To capture the events with in docker. Helpful for debug purpose
docker top <CONTAINER_ID> 												=> Running processes of a container
docker stats <CONTAINER_ID> 											=> Live stream of containers resource usage statistics


docker sytem df
docker sytem df -v 														=> to show docker disk usage


Docker Compose
==============
docker-compose -v
docker-compose --version
docker-compose version

docker-compose config													=> It will validate the docker-compose.yml file
docker-compose up -d 													=> run docker compose file in deattach mode
docker-compose down
