FROM node:14

WORKDIR /usr/src/app

COPY package*.json app.js ./

RUN npm i

EXPOSE 3001

CMD [ "node", "app.js" ]

#################################################################################
# sudo usermod -aG docker ${USER} && su - ${USER} && sudo systemctl status docker

# docker build -t kafka_docker . && docker run -d -p 3001:3001 --name node-app kafka_docker

# docker stop node-app && docker system prune -af

# docker ps
# docker exec -it node-app bash

#################################################################################
# RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app #
# USER node
# COPY --chown=node:node . .
