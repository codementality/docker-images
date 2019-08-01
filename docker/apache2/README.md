# Drupal tuned Apache image

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
