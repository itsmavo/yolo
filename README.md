# Overview
This project involved the containerization and deployment of a full-stack yolo application using Docker.


# Requirements
Install the docker engine here:
- [Docker](https://docs.docker.com/engine/install/) 

## How to launch the application 


![Alt text](image.png)

## How to run the app
Use 
```bash
vagrant up --provison command
```

## How to initialize Vagrant
from hashicorp registry pick the ubuntu/focal64 box
```bash
vagrant init ubuntu/focal64
```
## How to SSH into the Vagrant box
```bash
vagrant ssh or vagrant@127.0.0.1 -p 2222 -i ./path
```