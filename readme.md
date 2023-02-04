# Dockerizing a express web app

touch Dockerfile

- Add the following code to set the application’s base image using the FROM directive:

`FROM node:10-alpine`

- We will create the node_modules subdirectory inside the /home/node along with the app directory 
`mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app`

- Then you will set the working directory by adding the following line:
`WORKDIR /home/node/app`

- Add the following line to copy the package.json and package-lock.json files:

`COPY package*.json ./`

- Before running npm install, add the following line to switch the user to node
`USER node`

- Our container is now ready to run the npm install command. 
`RUN npm install`

- opy the application code into the application directory on the container with the right permissions
`COPY --chown=node:node . .`

- The last step is to expose the port 8090 on the container,
`EXPOSE 8090`
`CMD [ "node", "index.js" ]`




