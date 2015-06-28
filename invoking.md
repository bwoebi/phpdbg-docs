Invocation
==========

phpdbg is, by default, an interactive console program, invoked in the same way as the PHP interpreter:

    phpdbg /path/to/script.php

This does not execute the script, instead it opens an interactive prompt, ready to inspect and or execute ```/path/to/script.php```.

To execute the script:

    run

Usually, breakpoints should be set before ```run``` is executed.

Options
-------

phpdbg will accept the following options on the command line. Many of them are similar or the same than for the normal php cli interpreter. The others are specific to phpdbg, but usually not so important for basic debugging.

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
            <td>-q</td>
            <td>Suppress welcome banner (quiet)</td>
        </tr>
        <tr>
            <td><b>v</b></td>
            <td>-v</td>
            <td>Enable opline logging output (verbosity)</td>
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
            <td><b>p</b></td>
            <td>-p*</td>
            <td>Print opcode information (see below for further information)</td>
        </tr>
        <tr>
            <td><b>h</b></td>
            <td>-h</td>
            <td>Print the help</td>
        </tr>
        <tr>
            <td><b>V</b></td>
            <td>-V</td>
            <td>Print version number (version)</td>
        </tr>
    </tbody>
</table>

### Opcode printing (-p option) ###
There are a few options on how to print opcodes
* **-p** Outputs the main execution context
* **-p*** Outputs all opcodes in the whole file (including classes and functions)
* **-p=function_name** Outputs opcodes of a given function in the file
* **-p=class_name::** Outputs opcodes of all the methods of a given class
* **-p=class_name::method** Outputs opcodes of a given method

Initialization
--------------

When phpdbg is started, it will look for a file named ```.phpdbginit``` in the current directory. The path to ```.phpdbginit``` can be overridden with the ```-i``` option (see options).

A ```.phpdbginit``` file can contain phpdbg commands to execute, it can also contain code inline, follows is an example of an init file:

```
set prompt app>
<:
    /*
     Do something here in PHP to setup the debugging session
    */
    do_something_to_setup();
:>
```

Inline code must open with the tag ```<:``` on a line by itself, it must close with the tag ```:>``` on a line by itself.

Initialization can be used to bootstrap the session for debugging a particular framework, component, or application.
