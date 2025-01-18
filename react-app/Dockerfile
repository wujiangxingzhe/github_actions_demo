# Build stage
FROM node:20-alpine as build

# Set working directory
WORKDIR /react-app

# Copy package files
COPY public/ /react-app/public
COPY src/ /react-app/src
COPY package.json /react-app/package.json

# Install dependencies
RUN npm install

CMD ["npm", "start"]
