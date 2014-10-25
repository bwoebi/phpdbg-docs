The `ev` command
================

Phpdbg allows you to evaluate any arbitrary code you like with `ev`.

    prompt> ev 2 ** 3
    8

If you had a file `a.php` with contents `<?php $a = 10 ?>` and ran it:

    phpdbg a.php
    prompt> ev $a
    10

That way you can inspect the variables set by the file you have executed.

Further use
===========

Later when you have learned how to use breakpoints, you can inspect the whole environment, manipulate it to get information about the programs current state.

Environment in phpdbg will be preserved as long as you do not re-run the script.
