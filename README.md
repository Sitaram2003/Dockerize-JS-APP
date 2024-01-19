# Dockerize-JS-APP



This demo app shows a simple user profile app having details such as Name, Email and Interests

1. index.html with pure js and css styles
2. nodejs backend with express module
3. mongodb for data storage

All components are docker-based

> With Docker

To start the application
Step 1: Create docker network

# docker network create mongo-network 

Step 2(a): start mongodb

# docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    


Step 2(b): start mongo-express

# docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   

OR 

> With Docker Compose

To start the application
Step 1: start mongodb and mongo-express

# docker-compose -f docker-compose.yaml up

Step 2: open mongo-express from browser

# localhost:8081

Step 3: create user-account db and users collection in mongo-express
Step 4: Start your nodejs application locally - go to app directory of project

# npm install 
# node server.js

Step 5: Access you nodejs application UI from browser

# localhost:3000

step 6: To build a docker image from the application

# docker build -t my-app:1.0 .
( . indicates the location of docker file )

step 7: Rename the docker image by usinf tag command

# docker tag <old image name>:<tag> icr.io/<name space name>/<new image name>:<tag>

step 8: Login into the IBM Cloud CLI by using unique Command

step 9: Set the location as global 
Ensure that you're targeting the correct IBM Cloud Container Registry region.

# ibmcloud cr region-set global

step 10: Choose a name for your first namespace, and create that namespace. Use this namespace for the rest of the Quick Start.

# ibmcloud cr namespace-add <my_namespace>

step 11: Push the image to your private registry
1. Log your local Docker daemon into the IBM Cloud Container Registry.

# ibmcloud cr login

2. Choose a repository and tag by which you can identify the image. Use the same repository and tag for the rest of this Quick Start.

# docker tag my-js-app:v1 icr.io/<my_namespace>/my-js-app:1.0

4. Push the image.

# docker push icr.io/<my_namespace>/my-js-app:1.0

5. Verify that your image is in your private registry.

# ibmcloud cr image-list



