The `ev` command
================

phpdbg allows you to evaluate any arbitrary code with `ev` during execution:

    prompt> ev 2 ** 3
    8

You will be presented with a ```prompt>``` whenever phpdbg breaks: phpdbg will break when it hits a breakpoint, when a watch point is triggered, during stepping through code, or when PHP throws an uncaught exception.

Any valid PHP statement can be evaluated by ```ev```.
