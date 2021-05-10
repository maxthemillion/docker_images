This repository contains a collection of docker images built for data analysis purposes.
Builds are available from docker hub.

### image "rstan"
This image provides a functional rstan environment. It includes the [rethinking](https://github.com/rmcelreath/rethinking) packgage and its dependencies, which are required for working with the book ["Statistical Rethinking" by Richard McElreath](https://xcelab.net/rm/statistical-rethinking/)

### image "rstan jupyter"
This image adds a python installation based on miniconda to the rstan image (see above). It also installs an R-Kernel such that rstan can be run from jupyter.

##### Connecting to jupyter lab running container on vm
To open jupyter lab on localhost on your local machine follow these steps:

1. connect to vm (eg. Azure VM) via ssh:
> ssh -i ~/.ssh/mcmc.pem azureuser@>>publicip<< -p 50000 -L 9999:localhost:9999

2. run docker container on vm:
> $ docker run --rm -d -p 9999:9999 maxthemillion/rstan-jupyter:latest

then open https://localhost:9999 on your local machine

#### Connecting to jupyter running container locally
1. start docker container using
> $ docker run --rm -d -p 9999:9999 maxthemillion/rstan-jupyter:latest

##### Connecting to jupyter running container locally and including a bind mount
> $ docker run --rm -d -p 9999:9999 --mount type=bind,source="$(pwd)",target=/src/notebooks maxthemillion/rstan-jupyter:latest