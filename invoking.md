Invoking phpdbg
===============

phpdbg is, by default, an interactive console program, invoked in the same way as the PHP interpreter:

    phpdbg /path/to/script.php

This does not execute the script, instead it opens an interactive prompt, ready to inspect and or execute ```/path/to/script.php```.

To run the script:

    run
    
Usually, break or watch points should be set before ```run``` is executed.

*Note: phpdbg takes many of the same options that the PHP interpreter accepts.*
