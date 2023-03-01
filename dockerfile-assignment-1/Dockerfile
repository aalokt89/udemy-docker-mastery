FROM node:6-alpine

#install tini package
RUN apk add --no-cache tini

#make source directory
RUN mkdir -p /usr/src/app

#change working dir 
WORKDIR /usr/src/app

#copy json to image wrk dir
COPY package.json package.json

#install pkgs from json. && = coonditional. Will run if 1st cmd is successful.
RUN npm install && npm cache clean --force

#copy everything in the host directory to the image cwd.
COPY . .

# expose port 3000 for host
EXPOSE 3000

#start container with this cmd
CMD [ "/sbin/tini", "--", "node", "./bin/www" ]