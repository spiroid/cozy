# Cozy docker images

## What is this all about ?

Based on the really good work done by @obigroup and by @Kload, i spent some time to create smaller images for the cozy cloud plateform, based on the official cozy docker full image.
I like the full image because it just works out of the box, but i have this feeling that it's not the "docker way", or at least how i see it and want it to be.

That's why i started working on a more modular, decoupled approach with one process per docker image and a docker-compose recipe to link it all together.

This repository was created to centralize the work done on all the cozy docker images, as there is one github repository per image, and to bring together the documentation and docker-compose examples. Thanks to @woshilapin and @patcito for the idea  :)


## Quickstart

```
git clone git@github.com:spiroid/cozy.git
docker-compose up -d
```

## Initialization

When the container is running and your cozy cloud instance is not yet initialized, there is an init script to launch.
Given that your controller container name is cozy_controller_1 (docker-compose default) :

```
docker exec -it cozy_controller_1 cozy-init.sh
```

This installs the Home, Data-System and proxy applications, and could take a few minutes. Please be patient.
