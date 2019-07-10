[![Docker Stars](https://img.shields.io/docker/stars/alice2f/elivepatch-server.svg)](https://hub.docker.com/r/alice2f/elivepatch-server "Click to view the image on Docker Hub")
[![Docker Pulls](https://img.shields.io/docker/pulls/alice2f/elivepatch-server.svg)](https://hub.docker.com/r/alice2f/elivepatch-server "Click to view the image on Docker Hub")

**elivepatch-server-docker** is a docker instance for the [**server-side of elivepatch**](https://github.com/gentoo/elivepatch-server)

You can get the [**elivepatch client-side**](https://github.com/gentoo/elivepatch-client)

It handles the automated creation of live patch object for the Linux kernel (currently working only for gentoo-sources).

### Features:
* Automated creation of Live patch object using kpatch
* Client/Server configuration with the possibility of automated update
* SSL security configuration
* Supporting any gentoo-sources version and configuration
* Work with all versions of docker

## Basic usage

### Step 1 - start the elivepatch-server docker image
We added docker-compose.yml for a really simple usage.
```shell
$ docker-compose up -d
```
The previous command will start elivepatch server on the port 5000, where you can communicate with [**elivepatch-client**](https://github.com/gentoo/elivepatch-client).

### Step 2 - create a live patch object
Let's start by building a example live patch object.  
We can do it from the elivepatch-client repository like this.
```shell
 elivepatch-client -p example/2.patch -k example/config_5.1.6 -a 5.1.6 --url http://localhost:5000
```
## Additional documentation

Please check the [elivepatch wiki](https://wiki.gentoo.org/wiki/Elivepatch)
