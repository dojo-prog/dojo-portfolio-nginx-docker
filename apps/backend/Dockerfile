FROM node:22

WORKDIR /app

COPY package*.json ./
COPY apps/backend/package.json ./apps/backend/package.json
COPY packages/shared/package.json ./packages/shared/package.json

RUN npm install 

COPY apps/backend ./apps/backend
COPY packages/shared ./packages/shared

RUN npm run build -w @dojo-portfolio/backend

CMD ["npm", "start", "-w", "@dojo-portfolio/backend"]