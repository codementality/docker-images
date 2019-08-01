# Docker Images tuned for Acquia Cloud

[![Build Status](https://travis-ci.org/codementality/docker-images.svg?branch=develop)](https://travis-ci.org/codementality/docker-images)

This repository contains various Docker images tuned for project development on Acquia Cloud.  These images are hosted publicly on Docker Hub.

The purpose of these images is to provide a consistent set of Docker images for Drupal projects.  The images in this repository are built nightly via a cron job on Travis CI, and automatically deployed to Docker Hub on successful build.

## Base Images
There are two base images available that are used as the basis for every other image build:

* codementality/base -- Ubuntu 16.04 with some basic packages installed to support images dependent on this one
* codementality/php -- base image for PHP image builds.  This image is built on Ubuntu 16.04 (using codementality/base), and puts in place packages and infrastructure used to build the PHP images in this repo.

### codementality/base
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

### codementality/php
This image is based on codementality/base, and has the following additional applications installed:

* software-properties-common
* imagemagick
* graphicsmagick
* ghostscript
* jpegoptim
* libjpeg-turbo-progs
* pngcrush
* optipng
* apngopt
* pngnq
* pngquant
* mysql-client
* aptitude
* supervisor

This image also installs the popular repository ppa:ondrej/php, which is used to install PHP versions 7.1 through 7.3 on the respective PHP images below.

* Dockerfile: https://github.com/codementality/docker-images/blob/develop/docker/php/Dockerfile-php
* Docker Image Tags:  https://cloud.docker.com/u/codementality/repository/docker/codementality/php/tags

## Apache2 images

### codementality/apache2

The Apache2 image installs Apache 2.4 on Ubunut 16.04.  Apache has been configured with the following modules implemented:

* mod_actions 
* mod_proxy 
* mod_proxy_fcgi 
* mod_ssl 
* mod_rewrite
* mod_headers
* mod_expires

The default vhost file is configured to connect to a php-fpm container on port 9000 (see PHP images).

* Dockerfile: https://github.com/codementality/docker-images/blob/develop/docker/apache2/Dockerfile
* Docker Image Tags: https://cloud.docker.com/u/codementality/repository/docker/codementality/apache2/tags

## PHP Images

### All PHP Images
All PHP images install PHP from the ppa:ondrej/php package repository, and is built on the codementality/php base image.

PHP is installed as a FastCGI Process Manager (FPM) application.  These images expose port 9000 for connections.

The following applications are installed:
* gcc 
* make 
* autoconf 
* libc-dev 
* pkg-config 
* libmcrypt-dev
* mysql client

The following PHP extensions are also installed:
* php-fpm
* php-cli
* php-dev (for building PECL extensions)
* pear
* bcmath
* bz2
* calendar
* ctype
* curl
* dba
* dom
* exif
* fileinfo
* ftp
* gd
* gettext
* gmp
* gnupg
* http
* iconv
* igbinary
* imagick
* imap
* json
* ldap
* mbstring
* memcache
* memcached
* mysql
* oauth
* opcache
* pcntl
* pdo
* phar
* posix
* pspell
* radius
* shmop
* simplexml
* soap
* sockets
* solr
* ssh2
* sysvmsg
* sysvsem
* sysvshm
* tidy
* tokenizer
* uploadprogress
* wddx
* xdebug
* xml
* xmlreader
* xmlrpc
* xmlwriter
* xsl
* yaml
* zip

The current version of Composer is also installed.

### codementality/php7.3

* Dockerfile: https://github.com/codementality/docker-images/blob/develop/docker/php/Dockerfile-php7.3
* Docker Image Tags: https://cloud.docker.com/u/codementality/repository/docker/codementality/php7.3/tags

### codementality/php7.2

* Dockerfile: https://github.com/codementality/docker-images/blob/develop/docker/php/Dockerfile-php7.2
* Docker Image Tags: https://cloud.docker.com/u/codementality/repository/docker/codementality/php7.2/tags

### codementality/php7.1

* Dockerfile: https://github.com/codementality/docker-images/blob/develop/docker/php/Dockerfile-php7.1
* Docker Image Tags: https://cloud.docker.com/u/codementality/repository/docker/codementality/php7.1/tags
