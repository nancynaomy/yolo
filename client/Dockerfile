
FROM node:14-slim AS build

WORKDIR /app

COPY package*.json ./

RUN npm install --production && npm cache clean --force


COPY . .

RUN npm run build

FROM nginx:alpine AS production
WORKDIR /app
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 3000
CMD ["nginx", "-g"]
