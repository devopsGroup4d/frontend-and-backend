FROM node:16-alpine

WORKDIR /app

COPY package*.json package-lock.json ./

RUN npm install && ls -l /app/node_modules

COPY . .

EXPOSE 5000

CMD ["npm", "start"]
