# Cozy docker images

## Cozy

[Cozy](https://cozy.io) is a self-host personal open source data management solution. It is developed and promoted by a french startup named Cozy Cloud.

## Why another docker image ?

There is an official docker image created and maintained by the Cozy Cloud developers team: [cozy/full](https://hub.docker.com/r/cozy/full/). I like the full image because it just works out of the box, but i have this feeling that it's not done the "docker way", or at least not how i see it.

Based on the really good work done by @obigroup and by @Kload, i spent some time to create smaller images for the cozy plateform, based on the official cozy docker full image.

That's why i started working on a more modular, decoupled approach with one process per docker image and a docker-compose recipe to link it all together.

This repository was created to centralize the work done on all the cozy docker images, as there is one github repository per image, and to bring together the documentation and docker-compose examples. Thanks to @woshilapin and @patcito for the idea  :)

## Requirements

 * [docker](https://www.docker.com/) version 1.10+
 * [docker-compose](https://docker.github.io/compose/overview/) version 1.6.0+
 
## Quickstart


### Clone the repository

```
git clone git@github.com:spiroid/cozy.git
git checkout refactor-v2
```

### Configuration

Some of the containers configuration options are made available through environment variables. 
An easy way to get started is to create a .env file in the root folder where you cloned the repository:  

```
COUCHDB_USER=cozy
COUCHDB_PASSWORD=cozy
```

Please, Change the couchdb password value to a secret value of your choice.


### Run

```
docker-compose up -d
```

This will create 3 containers, a couchdb instance, the cozy controller and a pre configured nginx server that will act as a reverse proxy with a self signed ssl certificate.


### Initialization

When the container is running and your cozy cloud instance is not yet initialized, there is an init script to launch.
Given that your controller container name is cozy_controller_1 (docker-compose default) :

```
docker exec -it cozy_controller_1 cozy-init.sh
```

This installs the Home, Data-System and proxy applications, and could take a few minutes. Please be patient.


### Test

You should now open a browser and navigate to https://localhost/ accept the self signed certificate and enjoy your new cozy install :)


## Contributors

 * @obigroup
