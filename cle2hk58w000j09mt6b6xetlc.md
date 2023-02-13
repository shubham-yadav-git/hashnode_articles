# Docker Swarm Management

Docker Swarm is a native clustering and orchestration solution for Docker containers. It enables you to manage a group of Docker nodes as a single virtual system. With Docker Swarm, you can easily scale your applications, orchestrate the deployment of containers across a cluster, and manage their availability.

In this guide, we'll go through the steps to create, manage, and scale Docker services using Docker Swarm.

Step 1: Creating a Docker Network

The first step is to create a Docker network, which is a virtual network dedicated to your Docker containers. To create a Docker network, we use the following command:

```bash
docker network create -d overlay collabnet
```

The `-d` flag specifies the network driver, and `overlay` is the network driver we're using in this case. The `collabnet` argument is the name of the network.

Step 2: Listing Docker Networks

To see a list of Docker networks, use the following command:

```bash
docker network ls
```

Step 3: Inspecting a Docker Network

To get detailed information about a Docker network, use the following command:

```bash
docker network inspect collabnet
```

Step 4: Creating a Docker Service

A Docker service is a group of containers that run the same image and share the same network. To create a Docker service, we use the following command:

```bash
docker service create --name http --network collabnet --replicas 2 -p 80:80 ajeetraina/hellowhale
```

The `--name` flag specifies the name of the service, `http` in this case. The `--network` flag specifies the network the service should run on, `collabnet` in this case. The `--replicas` flag specifies the number of containers that should be running, 2 in this case. The `-p` flag maps a port on the host to a port in the container, in this case, port 80 to port 80 in the container. The `ajeetraina/hellowhale` argument is the image name.

Step 5: Listing Running Containers

To see a list of running containers, use the following command:

```bash
docker ps
```

Step 6: Testing the Docker Service

To test the Docker service, use the following command:

```bash
curl your_machine_ip:80
```

Step 7: Listing the Docker Service Tasks

To see a list of tasks running in a Docker service, use the following command:

```bash
docker service ps http
```

Step 8: Inspecting a Docker Service

To get detailed information about a Docker service, use the following command:

```bash
docker service inspect --pretty http
```

Step 9: Scaling a Docker Service

To change the number of containers running in a Docker service, use the following command:

```bash
docker service scale http=5
```

Step 10: Listing Docker Nodes

To see a list of Docker nodes, use the following command:

```bash
docker node ls
```

Step 11: Draining a Docker Node

To drain a Docker node, which means to stop scheduling new tasks on it, use the following command:

```bash
docker node update --availability drain worker2
```

Step 12: Inspecting a node

To view detailed information about a node run the following command:

```bash
docker node inspect --pretty worker2
```

Step 13: Make a drained node available again

```bash
docker node update --availability active worker2
```

Step 14: Removing the service sleep-app completely

```bash
docker service rm sleep-app
```

Step 15: Force the current node to leave the current swarm use the below command

```bash
docker swarm leave --force
```

In conclusion, these are the basic commands used to manage a docker swarm. You can refer to other blogs of the docker series to how to join a swarm and generate the swarm join token.

```bash
docker swarm join-token manager # It generates token to join as manager
docker swarm join-token worker # It generates token to join as the worker
```

One can easily practice these commands on the [docker playground](https://labs.play-with-docker.com/) and get a better understanding.