# Playing with docker, docker-compose, swarn

## Samples
###  python-sample1
This sample demonstrates how to pack simple python application as docker image and run it
```
cd python-sample1
docker build -t simple-python-app .
docker run --name hello-python -d --rm simple-python-app
```


## Good commands
* `docker ps -qa` - list IDs of all containers
* `docker rm $(docker ps -qa)` - remove all existing containers
* `docker rmi $(docker images -q)` - remove all existing images
