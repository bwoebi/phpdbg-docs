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
        <td><b>q</b></td>
        <td>&nbsp;</td>
        <td>Suppress welcome banner (quiet)</td>
    </tr>
    <tr>
        <td><b>v</b></td>
        <td>&nbsp;</td>
        <td>Enable opline logging output (verbosity)</td>
    </tr>
    <tr>
        <td><b>s</b></td>
        <td>&nbsp;</td>
        <td>Enable <b>s</b>tepping</td>
    </tr>
    <tr>
        <td><b>b</b></td>
        <td>&nbsp;</td>
        <td>Disable colours (boring)</td>
    </tr>
    <tr>
        <td><b>n</b></td>
        <td>&nbsp;</td>
        <td>Disable default php.ini (none)</td>
    </tr>
    <tr>
        <td><b>c</b></td>
        <td>-c/path/to/php.ini</td>
        <td>Set php.ini (config) file to load</td>
    </tr>
    <tr>
        <td><b>d</b></td>
        <td>-dmemory_limit=4G</td>
        <td>Set php.ini <b>d</b>irective</td>
    </tr>
    <tr>
        <td><b>i</b></td>
        <td>-i/path/to/init</td>
        <td>Set .phpdbginit script (init)</td>
    </tr>
</tbody>
</table>
