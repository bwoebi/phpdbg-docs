Building
========

Since PHP 5.6, phpdbg has been distributed with the source code of PHP. To configure the build process to compile the ```phpdbg``` binary, add the following configure switch:

    --enable-phpdbg

This will cause ```make``` to create the ```sapi/phpdbg/phpdbg```, subsequently ```make install``` will copy the ```phpdbg``` binary to the same path as the ```php``` binary.

Some distributions may package ```phpdbg``` separately from the ```php``` binary, some may not enable it at all: Refer to your package maintainer.

*phpdbg cannot be built independantly of the source code of PHP.*
