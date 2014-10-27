Besides `continue` and normal `step`, there exist four other commands how you can advance through code:
- step
- leave
- finish
- until

step
====

Step. Yes, again. There is not only line by line stepping, but also opcode-by-opcode stepping.

You might need it under some circumstances, when there's too much code on the current line and you cannot really follow it. Then step through it, it will show you in which order everything is executed. Or when something goes wrong due to a weird evalutaion order, which you need to debug.

Enabling it is as simple as

    set stepping opcode

or, with shortcuts

    s s opcode

Then each `step` command will just advance until the next opcode &mdash; instead of the next line.

To reset it later to line-by-line stepping:

    s s line

leave
=====

The leave command skips breakpoints until the VM encounters a ```return```.

Given the following code:

```
<?php
function foo() {
    $other = bar();
    
    return ["hello", $other];
}

function bar() {
    return "world";
}

foo();
?>
```

Here is an example session that uses the leave command:

    prompt> break foo
    [Breakpoint #0 added at foo]
    prompt> r
    [Breakpoint #0 in foo() at /usr/src/php-src/dbg.php:3, hits: 1]
    >00003:     $other = bar();
     00004:     
     00005:     return ["hello", $other];
    prompt> leave
    [Breaking for leave at /usr/src/php-src/dbg.php:5]
    >00005:     return ["hello", $other];
     00006: }
     00007:

As you can see, the first breakpoint at foo is hit, then the leave command is used to break at the next return statement.

Any breakpoints between the call to bar() and the return statement will be skipped.

finish
======

The finish command skips breakpoints until the current function is finished.

Given the following code:



until
=====

.....
