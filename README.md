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

```
git clone git@github.com:spiroid/cozy.git
git checkout refactor-v2
docker-compose up -d
```

## Initialization

When the container is running and your cozy cloud instance is not yet initialized, there is an init script to launch.
Given that your controller container name is cozy_controller_1 (docker-compose default) :

```
docker exec -it cozy_controller_1 cozy-init.sh
```

This installs the Home, Data-System and proxy applications, and could take a few minutes. Please be patient.


## Contributors

 * @obigroup
