#### Requirements

Download CentOS 7 base image:

```
docker pull centos:7
```

For more information about CentOS official docker images, please check here:

https://hub.docker.com/_/centos


#### Creating the deployment images

Create new deployment image:

```
docker build -t "omnidb:deploy_app_centos7" .
```


#### Compiling OmniDB

To compile OmniDB, start a container from the deployment image, and a shell into
the container:

```
docker run -it --rm omnidb:deploy_app_centos7 /bin/bash
```

Inside the container, run:

```
cd
./clone.sh
cd ~/OmniDB/OmniDB/deploy/app_centos7
./build.sh
```

Package will be on folder `~/OmniDB/OmniDB/deploy/packages`. Upload them to
somewhere else.

Because of the `--rm` above, the container will be automatically destroyed when
you exit the container shell.


#### Destroying the container

If you don't use `--rm` to create the container, you can destroy the container
anytime.

First you need to list the containers:

```
docker container ls
```

Then you can remove with:

```
docker container rm <container_id>
```


#### Destroying the image

You don't need to destroy the image, as it will be used for the next OmniDB
deployment.

To list all images:

```
docker images
```

You can destroy the image with:

```
docker image rm omnidb:deploy_app_centos7
```
