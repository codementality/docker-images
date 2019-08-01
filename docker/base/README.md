# Base Docker Image

This repository contains the base Docker image used for building the other containers in this repository.  This image is hosted on Docker Hub at https://hub.docker.com/r/codementality/base

## codementality/base
This image is based on Ubuntu 16.04, and has the following applications installed:

* ca-certificates 
* apt-transport-https 
* curl 
* wget 
* zip 
* unzip 
* bzip2 
* p7zip 
* rsync 
* git 
* lsb-release
* gosu release v1.10 (https://github.com/tianon/gosu)
* go-replace v1.1.2 (https://github.com/webdevops/goreplace)

This image is not intended to be used at the application level, but instead provides a basis for building other images.

The following Environment Variables are available for use in reconfiguring the Apache and PHP containers:

* WEB_DOCUMENT_INDEX:  defaults to `index.php`
* HOSTNAME:  defaults to container's hash
* WEB_DOCUMENT_ROOT:  default to `/var/www/html`
* PATH:  defaults to `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`
* WEB_PHP_SOCKET: defaults to `php:9000`
* WEB_ALIAS_DOMAIN: defaults to `*.vm`
* WEB_PHP_TIMEOUT: defaults to `600`

* Dockerfile: https://github.com/codementaity/docker-images/blob/develop/docker/base/Dockerfile
* Docker Image Tags: https://cloud.docker.com/u/codementality/repository/docker/codementality/base/tags
