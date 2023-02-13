# Docker Swarm Cheatsheet

These commands are used to manage a Docker Swarm cluster, create and manage Docker services, and manage Docker networks.

* `docker network create -d overlay collabnet` creates a new Docker overlay network named "collabnet".
    
* `docker network ls` lists all the available Docker networks.
    
* `docker network inspect collabnet` inspects the details of the "collabnet" network.
    
* `docker service create --name http --network collabnet --replicas 2 -p 80:80 ajeetraina/hellowhale` creates a new Docker service named "http" with 2 replicas, running the "ajeetraina/hellowhale" image and connected to the "collabnet" network. Port 80 is exposed on the host and maps to port 80 in the container.
    
* `docker ps` lists all the running containers.
    
* `curl your_machine_ip:80` sends a request to the IP address "your\_machine\_ip" on port 80.
    
* `docker service ps http` shows the status of the "http" service.
    
* `docker service inspect --pretty http` inspects the details of the "http" service.
    
* `docker node ps self` shows the tasks running on the current node.
    
* `docker node ps $(docker node ls -q | head -n1)` shows the tasks running on the first node in the cluster.
    
* `docker service scale http=5` scales the number of replicas of the "http" service to 5.
    
* `curl your_machine_ip:80` sends another request to the IP address "your\_machine\_ip" on port 80.
    
* `docker service scale http=2` scales the number of replicas of the "http" service back to 2.
    
* `docker service create --name sleep-app ubuntu sleep infinity` creates a new Docker service named "sleep-app" with a single replica running the "ubuntu" image and running the "sleep infinity" command.
    
* `docker service update --replicas 7 sleep-app` updates the number of replicas of the "sleep-app" service to 7.
    
* `docker service ls` lists all the available Docker services.
    
* `docker service ps sleep-app` shows the status of the "sleep-app" service.
    
* `docker service update --replicas 4 sleep-app` updates the number of replicas of the "sleep-app" service back to 4.
    
* `docker node ls` lists all the nodes in the Swarm cluster.
    
* `docker node update --availability drain worker2` drains the node "worker2" so that no new tasks will be scheduled on it.
    
* `docker node inspect --pretty worker2` inspects the details of the "worker2" node.
    
* `docker node update --availability active worker2` reactivates the "worker2" node so that it can again receive tasks.
    
* `docker service rm sleep-app` removes the "sleep-app" service.
    
* `docker service ls` lists all the available Docker services.
    
* `docker kill yourcontainerid` kills the container with the ID "yourcontainerid".
    
* `docker swarm leave --force` forces the current node to leave the Swarm cluster.
    
* `docker swarm join-token manager` retrieves the command to join the Swarm cluster as a manager.
    
* `docker network create --driver=overlay --subnet=192.168.1.0/24 --gateway=192.168.1.100 myoverlay0` creates network of overlay type with specified subnet and gateway.