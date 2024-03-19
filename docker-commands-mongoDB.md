
#  create docker network
## containers in the same network can communicate my using container Name 
docker network create mongo-network

docker run -d \
-p 27017:27017 \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONGO_INITDB_ROOT_PASSWORD=pass \
--name mongodb \
--net mongo-network \
mongo:4.0.28


docker run -d \
-p 8081:8081 \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=pass \
-e ME_CONFIG_MONGODB_SERVER=mongodb \
--net mongo-network --name mongo-express \
mongo-express 
