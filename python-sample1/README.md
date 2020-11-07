###  How to run
This sample demonstrates how to pack simple python application as docker image and run it
Go to `python-sample1` and run:
* `docker build -t simple-python-app .` to build the image
* `docker image ls | grep python` to see the images like "*python*"
* `docker run --rm simple-python-app` to run the container from the image
* `docker run --name hello-python -d --rm simple-python-app` to run the named container from the image

## Good commands
* `docker ps -qa` - list IDs of all containers
* `docker rm $(docker ps -qa)` - remove all existing containers
* `docker rmi $(docker images -q)` - remove all existing images
