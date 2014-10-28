About inspecting
================

Breaking? Why? I can `ev` something, but does that really give me any advantage over putting a simple `var_dump()` statement into code?

But, wait. There are other commands too. Like `info` with all its subcommands. And `back` which gives you a backtrace (just like `debug_print_backtrace()`).

Or ever wondered why a method was called at a time when it shouldn't have been? Break at that method then and use the `frame` command which allows you to navigate through the stack to inspect the environment variables.

back
----

A trivial backtace, numbered from #0 in current stack frame (current function or file you're executing) to the last one which always is {main}, the starting point of your script.

Simple example: (shortcut is `t`)

    > t
    ... find here some nice trace to post ...

frame
-----

The `frame` command will allow you to switch a stack frame you want to inspect. The syntax of the frame command is fairly simple:

    frame 5

where 5 is the number of the frame you've gotten from `back` command before.

info
----

...
