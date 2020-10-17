# Example of 3 simple node servers in different networks
* testnode1 in network1 
* testnode2 in network1 & network2 
* testnode3 in network2

### How to use 
* `docker-compose up -d` - to run 3 containers for node servers
* `docker network ls` to list all available Docker's networks
  * as result bridge, host and our network1 and network2 should be listed 
* `docker inspect network1 network2` to inspect our network1 and network2
  * `docker inspect -f '{{range.IPAM.Config}}{{.Subnet}}{{end}}' network1 network2` to inspect with `subnet' information via GO-template
* `docker ps --format {{.ID}}\t{{.Names}}` to list all containers with their identifiers
  * `docker inspect CONTAINER_ID --format {{.NetworkSettings.Networks.network1.IPAddress}}` to inspect container
* `docker exec CONTAINER_ID cat /etc/hosts` to print hosts directly from a container using the docker exec command:
* by having container_id and it IP address we can check it by using `curl` with IP address or alias, since we're inside the Docker's network
```
docker exec -it b3fe48bbddd6 /bin/bash
root@b3fe48bbddd6:/# curl 172.19.0.3:9080
Hello from test1
root@b3fe48bbddd6:/# curl testnode1:9080
Hello from test1
``` 
* mind that we can't connect to the “testnode3” container from network1 because it's in a different network. Connecting by the IP address will time out:
  * connecting by the alias will also fail because the DNS service won't recognize it
* To make this work, we need to add “testnode3” container to “network1” (from outside of the container):
  `docker network connect --alias testnode3 network1 CONTAINER_ID_FROM_ANOTHER_NETWORK`
