# Docker

## Introduction

Docker is a technology that helps make computer programs work better. It does this by putting the program and everything it needs to run (like libraries and other files) into a special package called a container. This makes it easier to run the program on different computers and share it with others. Think of a container like a special room for your program to run in, so it has everything it needs and nothing extra.

## Most used commands

Here are some of the most commonly used Docker commands, along with a brief explanation of each:

1. `docker run`: This command is used to run a Docker container from an image. The format of the command is: `docker run [options] image_name [command]`.
    
2. `docker pull`: This command is used to download an image from a Docker registry. The format of the command is: `docker pull image_name`.
    
3. `docker ps`: This command is used to list the containers that are currently running on a system. The format of the command is: `docker ps [options]`.
    
4. `docker images`: This command is used to list the images that are stored locally on a system. The format of the command is: `docker images [options]`.
    
5. `docker inspect`: This command is used to inspect the properties of a container or an image. The format of the command is: `docker inspect [options] object_name`.
    
6. `docker rm`: This command is used to remove one or more containers. The format of the command is: `docker rm [options] container_name`.
    
7. `docker rmi`: This command is used to remove one or more images. The format of the command is: `docker rmi [options] image_name`.
    
8. `docker build`: This command is used to build a Docker image from a Dockerfile. The format of the command is: `docker build [options] path`.
    
9. `docker login`: This command is used to log in to a Docker registry. The format of the command is: `docker login [options] [registry_url]`.
    
10. `docker push`: This command is used to upload an image to a Docker registry. The format of the command is: `docker push [options] image_name`.
    

These commands provide a good starting point for working with Docker, but there are many more commands available. You can find more information and a full list of commands in the Docker documentation.