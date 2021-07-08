# BUILD PHASE
FROM node:alpine

# Correções erro cache
# USER node
# RUN mkdir -p /home/node/app

# Working directory
WORKDIR '/app'

# Copy package.json to current WORKDIR
COPY package.json .
# COPY --chown=node:node ./package.json ./

# Install dependencies
RUN npm install

# Copy everything over to project directory
COPY . .
# COPY --chown=node:node ./ ./

RUN npm run build

# RUN PHASE
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html
