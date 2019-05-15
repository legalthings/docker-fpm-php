LegalThings fpm-php
================

Base docker image to run PHP applications on with FPM


Building the base image
-----------------------

To create the base image `legalthings/fpm-php`, execute the following command (replace <php-version> with the desired version):

    docker build -t legalthings/fpm-php:<php-version> -f <php-version>/Dockerfile .

Loading your custom PHP application
-----------------------------------

This image can be used as a base image for your PHP application. Create a new `Dockerfile` in your
PHP application folder with the following contents:

    FROM legalthings/fpm-php:<php-version>
