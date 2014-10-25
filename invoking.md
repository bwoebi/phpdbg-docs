Invocation
==========

phpdbg is, by default, an interactive console program, invoked in the same way as the PHP interpreter:

    phpdbg /path/to/script.php

This does not execute the script, instead it opens an interactive prompt, ready to inspect and or execute ```/path/to/script.php```.

To execute the script:

    run
    
Usually, break or watch points should be set before ```run``` is executed.

Options
-------

phpdbg will accept the following options on the command line:

<table>
<thead>
    <tr>
        <th>Option</th>
        <th>Example</th>
        <th>Purpose (name)</th>
    </tr>
</thead>
<tbody>
    <tr>
        <td><b>q</b></td>
        <td>-b</td>
        <td>Suppress welcome banner (quiet)</td>
    </tr>
    <tr>
        <td><b>v</b></td>
        <td>-v</td>
        <td>Enable opline logging output (verbosity)</td>
    </tr>
    <tr>
        <td><b>s</b></td>
        <td>-s</td>
        <td>Enable stepping (stepping)</td>
    </tr>
    <tr>
        <td><b>b</b></td>
        <td>-b</td>
        <td>Disable colours (boring)</td>
    </tr>
    <tr>
        <td><b>n</b></td>
        <td>-n</td>
        <td>Disable default php.ini (none)</td>
    </tr>
    <tr>
        <td><b>c</b></td>
        <td>-c/path/to/php.ini</td>
        <td>Set php.ini file to load (config)</td>
    </tr>
    <tr>
        <td><b>d</b></td>
        <td>-dmemory_limit=4G</td>
        <td>Set php.ini directive (directive)</td>
    </tr>
    <tr>
        <td><b>i</b></td>
        <td>-i/path/to/init</td>
        <td>Set .phpdbginit script (init)</td>
    </tr>
    <tr>
        <td><b>I</b></td>
        <td>-I</td>
        <td>Ignore default .phpdbginit (ignore)</td>
    </tr>
    <tr>
        <td><b>O</b></td>
        <td>-O/path/to/log</td>
        <td>Set opline logging output file (oplog)</td>
    </tr>
    <tr>
        <td><b>r</b></td>
        <td>-r</td>
        <td>Run immediately (run)</td>
    </tr>
    <tr>
        <td><b>rr</b></td>
        <td>-rr</td>
        <td>Run immediately, then exit (run and retract)</td>
    </tr>
    <tr>
        <td><b>E</b></td>
        <td>-E</td>
        <td>Enable stepping through eval'd code (evil)</td>
    </tr>
    <tr>
        <td><b>S</b></td>
        <td>-Scli</td>
        <td>Override SAPI name (sapi)</td>
    </tr>
    <tr>
        <td><b>l</b></td>
        <td>-l4000</td>
        <td>Set remote console port (listen)</td>
    </tr>
    <tr>
        <td><b>a</b></td>
        <td>-a192.168.0.2</td>
        <td>Set remote console address (address)</td>
    </tr>
    <tr>
        <td><b>V</b></td>
        <td>-V</td>
        <td>Print version number (version)</td>
    </tr>
</tbody>
</table>
