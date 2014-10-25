Invoking phpdbg
===============

phpdbg is, by default, an interactive console program.

phpdbg is invoked in the same way as the PHP interpreter:

    phpdbg /path/to/script.php
    
*Note: phpdbg takes many of the same options that the PHP interpreter accepts.*

This does not execute the script, instead it opens an interactive prompt, ready to inspect and or execute ```/path/to/script.php```.

To run the script:

    run
    
Usually, break or watch points should be set before ```run``` is executed.
