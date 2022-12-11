FROM node:19-slim

WORKDIR /manager
COPY package*.json ./
RUN npm install
COPY . .
CMD ["npm", "start"]
