# Drupal tuned php images
This directory contains Dockefiles and build scripts for the following php-fpm images:

* codementality/php
* codementality/php7.1
* codementality/php7.2
* codementality/php7.3

All images above are the "latest", with images also tagged with Ubuntu16.04 and minor Ubuntu version updates, and pushed to Docker Hub.

These images are build based on the codementality/base image, which is an Ubuntu 16.04 image.  These images are designed to be used with either NginX or Apache2, running PHP as a service.

These images are automatically built daily, and pushed up to Docker Hub with updates.  As Ubuntu 16.04 releases minor versions, updates to the codementality/base image as well as the codementality/php{version} images are automatically tagged appropriately and pushed up to Docker Hub.  This preserves the previously built image versions so that images can be pinned in a docker-compose.yml file for a specific project if needed.

To utilize a specific PHP version built on a specific minor version image, use an image tag in your docker-compose.yml file as follows:
* codementality/php7.3:ubuntu-16.04.6

If you tag an image as follows:

* codementality/php7.3:ubuntu-16.04

You will be using the latest Ubuntu-16.04 build.

Tagging an image as follows:

* codementality/php7.3

Will get you the latest php7.3 image build.  Currently this is the same as using:

* codementality/php7.3:ubuntu-16.04

## codementality/php
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

