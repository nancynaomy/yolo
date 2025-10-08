# Project Explanation (YOLO Dockerized App)
## Overview

### What’s in this project?
This document breaks down what’s in the repo, how everything works with Docker, how to run the app locally, and some useful tips to troubleshoot or optimize your setup.

Here’s an overrview of what each part of the repo does:

1. `client/ –` The front-end built with React. Includes its own Dockerfile for building a production-ready container.

2. `backend/` – Node.js/Express server with routes, file upload utilities, and Mongoose models.

3. `roles/` – Ansible deployment roles (not yet covered, you can ignore this if you’re just running locally with Docker).

4. `compose.yml` – Docker Compose file that ties together the client, backend, and database.

5. `.env` – Stores environment variables. There’s a sample provided in the repo. Rename it and update variables

### How the Docker setup works

The `client Dockerfile` uses a multi-stage build:

 - First stage: installs dependencies and builds the React app.

 - Final stage: copies the production build into a small node:alpine image.

The backend has its own `Dockerfile` with a similar setup — simple, clean, and lightweight.

Everything is wired up using Docker Compose (`compose.yml`), which also pulls in environment variables from .env.

## Manually building the Docker images
If you want to build the images manually (outside of Compose) or to test each build, run these from the root of the repository:

```bash 
# Build the front-end image
docker build -t nancynaomy/naomi-yolo-client:v1.0.0 client/

# Build the back-end image
docker build -t nancynaomy/naomi-yolo-backend:v1.0.0 backend/
```

## Running the full app with Docker Compose
Use below commands to run and stop containers
```bash 
# Build all services and run them in the foreground
docker compose up --build

# Stop and clean up and remove volume attached
docker compose down -v

# Check logs for a specific service (e.g., the nancynaomy/naomi-yolo-client:v1.0.0)
docker compose logs -f nancynaomy/naomi-yolo-client:v1.0.0
```
## Environment variables (.env)
- `MONGO_URI` – MongoDB connection string used by the backend.

- `PORT` – The port the backend server runs on.

- `MONGO_INITDB_ROOT_USERNAME / MONGO_INITDB_ROOT_PASSWORD` – Credentials for MongoDB when using Docker.

## Common issues & how to fix them

1. Permission errors with node_modules

- If the image fails while trying to write to cache or modules:

- Set a proper working directory in your Dockerfile

2. Large image size.
If your image is huge:
- Add a .dockerignore to keep out things like node_modules, .git, etc.

