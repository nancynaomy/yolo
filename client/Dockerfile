
FROM node:14-slim AS build

# container working directory
WORKDIR /app

COPY package*.json ./

RUN npm install --production && npm cache clean --force


COPY . .
# builing phase
RUN npm run build

# using nginx for serving static files in production(small image size)
FROM nginx:alpine AS production

WORKDIR /app

COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 3000

CMD ["nginx", "-g", "daemon off;"]
