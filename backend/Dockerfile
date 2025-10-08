# Use an official Node runtime as a parent image
FROM node:10-alpine AS build

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the pall package.json files to the container
COPY package*.json ./

# Install application dependencies
RUN npm install

COPY . .

# Adding  multi-stage build
FROM alpine:3.16.7

WORKDIR /app

RUN apk update && apk add --update nodejs

COPY --from=build /usr/src/app /app

# port app runs on
EXPOSE 500

# run app
CMD ["node", "server"]
