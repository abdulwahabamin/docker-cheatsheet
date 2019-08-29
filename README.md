# Docker-cheatsheet
#### Build a Docker image
$ docker build -t [image_name]:[tag] .
#### Run a Docker container specifying a name
$ docker run --name [container_name] [image_name]:[tag]
#### Fetch the logs of a container
$ docker logs -f [container_id_or_name]
#### Run a command in a running container
$ docker exec -it [container_id_or_name] bash
#### Show running containers
$ docker ps
#### Show all containers
$ docker ps -a
#### Show Docker images
$ docker images
#### Stop a Docker container
$ docker stop [container_id_or_name]
#### Remove a Docker container
$ docker rm [container_id_or_name]
#### Remove a Docker image
$ docker rmi [image_id_or_name]
#### Docker jupyter notebook
$ docker run -it --rm -p 8080:8080 image </br>
$ jupyter notebook --ip 0.0.0.0 --no-browser --allow-root </br>
#### Docker tensorflow run
Need nvidia-docker installed to run gpu on containers <br/>
Nvidia-docker: https://github.com/NVIDIA/nvidia-docker/wiki/Installation-(version-2.0) <br/>
$ docker run --runtime=nvidia -it --rm tensorflow/tensorflow:devel-gpu-py3 bash <br/>
