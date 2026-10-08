FROM node:22 AS build 

WORKDIR /app

COPY package*.json ./
COPY apps/web/package.json ./apps/web/package.json
COPY packages/shared/package.json ./packages/shared/package.json

RUN npm install 

COPY apps/web ./apps/web
COPY packages/shared ./packages/shared

RUN npm run build -w @dojo-portfolio/web -- --mode docker

FROM node:alpine 

COPY --from=build /app/apps/web/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

