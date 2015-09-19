Besides `continue` and normal `step`, there exist four other commands how you can advance through code:
- step
- next
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

next
====

We have step, but it steps *into* eventually encountered functions. Now, there is the next command, able to step *over* lines.

If you use the next command, you never will land in functions deeper in the call stack.

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

As you see, when you are in `foo()` function while using `next`, you'll never run into `bar()`, but skip right over it:

```
prompt> break foo
[Breakpoint #0 added at foo]
prompt> r
[Breakpoint #0 in foo() at /Users/Bob/php-src-X/test.php:3, hits: 1]
>00003:     $other = bar();
 00004:     
 00005:     return ["hello", $other];
prompt> next
[L5          0x10f066560 INIT_ARRAY              "hello"                                   ~2                   /Users/Bob/php-src-X/test.php]
>00005:     return ["hello", $other];
 00006: }
 00007: 
prompt> n
[L5          0x10f0665a0 RETURN                  ~2                                                             /Users/Bob/php-src-X/test.php]
[L12         0x10f06b140 RETURN                  1                                                              /Users/Bob/php-src-X/test.php]
>00012: foo();
 00013: 
prompt> 
[Script ended normally]
```

leave
=====

The leave command skips breakpoints until the VM encounters a `return`.

Here is an example session that uses the leave command, with the same code already used for the next command:

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

```
prompt> b bar
[Breakpoint #0 added at bar]
prompt> b 5
[Breakpoint #1 added at /Users/Bob/php-src-X/test.php:5]
prompt> r
[Breakpoint #0 in bar() at /Users/Bob/php-src-X/test.php:9, hits: 1]
>00009:     return "world";
 00010: }
 00011: 
prompt> finish
[Breakpoint #1 at /Users/Bob/php-src-X/test.php:5, hits: 1]
>00005:     return ["hello", $other];
 00006: }
 00007: 
```

As one can see here, it is similar to the leave command, but it does *not* add an extra breakpoint at the end of the function.

until
=====

.....
