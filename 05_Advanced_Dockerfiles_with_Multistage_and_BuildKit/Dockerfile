FROM node:10-slim as prod
#FROM node:14.7-slim as prod
ENV NODE_ENV=production
# optional : WORKDIR /app
COPY package*.json ./
RUN npm install --only=production && npm cache clean --force 
COPY . . 
CMD ["node", "./bin/www"]

FROM prod as dev
ENV NODE_ENV=development
RUN npm install --only=development
CMD ["../node_modules/nodemon/bin/nodemon.js", "./bin/www", "--inspect=0.0.0.0:9229"] 

FROM dev as test
ENV NODE_ENV=test
CMD ["npm", "test"]
