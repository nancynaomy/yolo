# Overview
This project involved the containerization and deployment of a full-stack yolo application using Docker.


# Requirements
Install the docker engine here:
- [Docker](https://docs.docker.com/engine/install/) 


## How to Build each Container
Before you start Ensure you're logged in to docker hub
### 1. Client Dockerfile
Create clients Dockerfile and test the build using this command
```bash
docker build -t nancynaomy/naomi-yolo-client:v1.0.0 client/
```
![alt text](image-1.png)
The image size is quite big and we need to reduce the size.
Tested several images and working with `alpine:3.16.7`  gives us a small image
![alt text](image-2.png)

Further testing reduced my image to 60.9mb
![alt text](image-3.png)

### 2. Backend Docker 

Like client Dockerfile, use below command to build the image 
```bash
docker build -t nancynaomy/naomi-yolo-backend:v1.0.0 backend/
```
The image is created Succesfully.
![alt text](image-4.png)

## Docker-compose

create docker compose file on the root folder.
```bash yolo
          |__ compose.yaml 
```
1. Create client container(as a service inside container)
 - Bind Port 

        ```bash 
                ports:
              - "3000:3000"
        ```
 - specify building dir
 - Attach Network

 2. Create backend container similar to client and attach to the same network
 3. Create a database container and connect it to backend container using a different network
 