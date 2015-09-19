Building phpdbg with PHP
========================

phpdbg needs to be built at the same time as the PHP source. It is enabled by default (since PHP 7).

The configure switch is needed for PHP 5.6:

    --enable-phpdbg

Building phpdbg with an old version of PHP
==========================================

phpdbg can be used with PHP from version 5.4.

To build phpdbg for an old version of PHP, assuming ```/usr/src/php-src``` contains the source code to PHP:

    cd /usr/src/php-src
    git clone https://github.com/krakjoe/phpdbg sapi/phpdbg
    ./buildconf --force
    ./configure [normal build options here] --enable-phpdbg

`make install` will install the ```phpdbg``` in the same directory as other binaries.
