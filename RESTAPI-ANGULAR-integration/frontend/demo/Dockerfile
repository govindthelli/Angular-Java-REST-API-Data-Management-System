#STAGE 1

FROM node:18 AS build

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build

#STAGE 2

FROM nginx:1.25-alpine

RUN rm /etc/nginx/conf.d/default.conf

COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=build /app/dist/demo /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]