Invoking phpdbg
===============

phpdbg is, by default, an interactive console program, invoked in the same way as the PHP interpreter:

    phpdbg /path/to/script.php

This does not execute the script, instead it opens an interactive prompt, ready to inspect and or execute ```/path/to/script.php```.

To run the script:

    run
    
Usually, break or watch points should be set before ```run``` is executed.

phpdbg options
--------------

<table>
<thead>
    <tr>
        <th>Option</th>
        <th>Example</th>
        <th>Purpose</th>
    </tr>
</thead>
<tbody>
    <tr>
        <td>*c*</td>
        <td>-c/path/to/php.ini</td>
        <td>Set php.ini file to load</td>
    </tr>
    <tr>
        <td>*c*</td>
        <td>-c/path/to/php.ini</td>
        <td>Set php.ini file to load</td>
    </tr>
</tbody>
</table>
