# Overview
This project involved the containerization and deployment of a full-stack yolo application using Docker.


# Requirements
Install the docker engine here:
- [Docker](https://docs.docker.com/engine/install/) 

## How to launch the application 


![Alt text](image.png)

## How to run the app
Use vagrant up --provison command


## How to Build each Container
### 1. Client Dockerfile
Create clients Dockerfile and test the build using this command
```bash
docker build -t client_image:v1.0 .
```
![alt text](image-1.png)
The image size is quite big and we need to reduce the size.
