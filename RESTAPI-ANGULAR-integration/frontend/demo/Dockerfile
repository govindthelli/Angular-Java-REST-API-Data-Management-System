#stage 1 building
FROM node:18-slim AS build

WORKDIR /app

COPY package*.json ./

RUN npm install 

COPY . .

RUN npm run build

#stage 2 serving
FROM nginx:1.2-alphine

WORKDIR /app

COPY --from=build /dist/demo/* /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
