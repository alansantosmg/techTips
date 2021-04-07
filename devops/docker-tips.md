# Docker

## Docker install

### How to install Docker on ubuntu

`sudo apt-get install docker.io`

### Checking docker install

```bash

sudo docker --version
sudo docker machine -- version
sudo docker composer --version

sudo docker container run hello-world 

```

## Getting help

`docker help`

## Basic commands

```bash

// Get images list
sudo docker images

// Get images list - alternate
sudo docker image list

// Get or update images (getting a python image)
sudo docker pull python


// Inspect docker got image
sudo docker image inspect
```


