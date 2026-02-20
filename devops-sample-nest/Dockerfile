FROM node:20-alpine AS builder


WORKDIR /app


COPY package.json ./
COPY package-lock.json ./

RUN npm install

COPY . .

RUN npm run build


FROM node:20-alpine

WORKDIR /app

COPY --from=builder /app/dist ./dist
COPY package.json ./
COPY package-lock.json ./

RUN npm install --production

EXPOSE 3000

CMD ["node","dist/main.js"]
