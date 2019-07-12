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

## Basic development

### Step 1 - Move to the development enviroment
```shell
$ git checkout development
```

### Step 2 - Rebuild image if necessary
```shell
$ docker-compose build
```

### Step 3 - Clone elivepatch-server repository
We need to clone the elivepatch-server repository that we want to work on.  
In this case we are using the official repository as example but you can use a fork.
```shell
$ git clone git@github.com:gentoo/elivepatch-server.git elivepatch-server
```

### Step 4 - Make some changes

### Step 5 - Test everything is working
```shell
$ docker-compose up -d
$ docker-compoes exec gentoo /bin/bash
bbd875c1561b /elivepatch_development $ python setup.py install
bbd875c1561b /elivepatch_development $ elivepatch-server -d
```

### Step 6 - create a live patch object
Let's start by building a example live patch object.  
We can do it from the elivepatch-client repository like this.
```shell
 elivepatch-client -p example/2.patch -k example/config_5.1.6 -a 5.1.6 --url http://localhost:5000
```

### Step 7 - Send a pull request
Feel free to send pull requests to elivepatch-server or elivepatch-client.
Welcome to the project.

## Additional documentation

Please check the [elivepatch wiki](https://wiki.gentoo.org/wiki/Elivepatch)
