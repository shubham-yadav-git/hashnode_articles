# Docker

## Introduction

Docker is a technology that helps make computer programs work better. It does this by putting the program and everything it needs to run (like libraries and other files) into a special package called a container. This makes it easier to run the program on different computers and share it with others. Think of a container like a special room for your program to run in, so it has everything it needs and nothing extra.

### VM v/s Docker

A Virtual Machine (VM) and Docker are both technologies used for application virtualization, but they work differently and have different use cases.

A *Virtual Machine runs a complete operating system, including the kernel, on top of physical hardware or a host operating system*. This provides a fully isolated environment for the application to run, with its own set of resources and virtualized hardware. VMs are useful for running multiple operating systems on the same physical hardware, and for testing and development purposes.

Docker, on the other hand, *uses a container-based approach to virtualization. Instead of running a complete operating system, Docker containers share the host operating system kernel and only include the application and its dependencies.*This makes containers lighter and faster to start than VMs, as they don't need to boot a complete operating system. Containers are also more portable and efficient, as they can be easily moved between host systems and don't require their own set of virtualized resources.

While both VMs and Docker provide virtualization and isolation for applications, they differ in terms of resource utilization, portability, and performance. VMs are better suited for running multiple operating systems and for more complex applications, while Docker containers are more suitable for lighter and faster application deployments.

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