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
#### Docker copy file from host to root
$ docker file/location/in/base/os container-id:/file-location </br>
#### Docker tensorflow run
Need nvidia-docker installed to run gpu on containers <br/>
Nvidia-docker: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker <br/>
$ docker run --runtime=nvidia -it --rm tensorflow/tensorflow:devel-gpu-py3 bash <br/>
#### Docker cv2 window (accessing windows on host)
$ xhost + && docker run --rm -ti --net=host --ipc=host -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --device /dev/dri:/dev/dri -v volume/to/mount docker-image:tag
#### Docker volume mount to local host
Create a volume from terminal <br/>
$ docker volume create --driver local --opt type=none --opt device=/home/user/test --opt o=bind test_vol <br/> 
Create a volume in docker-compose file </br>
volumes:
    bind-test: \
      driver: local \
      driver_opts: \
        type: none \
        o: bind \
        device: /home/user/test \
NOTE: In docker compose, volume doesn't create a local directory on the host. You have to make sure that the directory exists otherwise the mount will fail
