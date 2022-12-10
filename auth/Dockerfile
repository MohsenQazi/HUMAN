FROM node:19-slim

WORKDIR /authenticator
COPY package*.json ./
RUN npm install
COPY . .
CMD ["npm", "start"]
