
# Overview
This project demonstrates the containerization and deployment of a full-stack YOLO application using Docker.



# Requirements
Install Docker Engine by following the instructions here:
- [Docker Installation Guide](https://docs.docker.com/engine/install/)



## Building Each Container
Before you start, ensure you are logged in to Docker Hub.

### 1. Client Dockerfile
Create the client Dockerfile and test the build with the following command:
```bash
docker build -t nancynaomy/naomi-yolo-client:v1.0.0 client/
```
![Client Build Output](image-1.png)

The initial image size may be large, so optimization is recommended. After testing several base images, using `alpine:3.16.7` resulted in a significantly smaller image:
![Optimized Image Output](image-2.png)

With further optimization, the image size was reduced to 60.9 MB:
![Final Optimized Image](image-3.png)

### 2. Backend Docker

Similarly, to build the backend image, use the following command:
```bash
docker build -t nancynaomy/naomi-yolo-backend:v1.0.0 backend/
```
The image is created successfully:
![Backend Build Output](image-4.png)


## Docker Compose

Create a `docker-compose.yaml` file in the root folder:

```
yolo/
|__ compose.yaml
```

1. Define the client container as a service:
   - Bind the port:
     ```yaml
     ports:
       - "3000:3000"
     ```
   - Specify the build directory
   - Attach to a network

2. Define the backend container similarly and attach it to the same network.
3. Define a database container and connect it to the backend container using a separate network.
