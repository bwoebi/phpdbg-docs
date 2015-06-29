About inspecting
================

Breaking? Why? I can `ev` something, but does that really give me any advantage over putting a simple `var_dump()` statement into code?

But, wait. There are other commands too. Like `info` with all its subcommands. And `back` which gives you a backtrace (just like `debug_print_backtrace()`).

Or ever wondered why a method was called at a time when it shouldn't have been? Break at that method then and use the `frame` command which allows you to navigate through the stack to inspect the environment variables.

back
----

A trivial backtrace, numbered from #0 in current stack frame (current function or file you're executing) to the last one which always is {main}, the starting point of your script.

Simple example: (shortcut is `t`)

    > t
    ... find here some nice trace to post ...

frame
-----

The `frame` command will allow you to switch a stack frame you want to inspect. The syntax of the frame command is fairly simple (shortcut is `f`):

    > frame 5
    [Switched to frame #5]

where 5 is the number of the frame you've gotten from `back` command before.

In that frame you now can get the current variables and even manipulate context (via `ev`).

> Note that when not in top-frame, certain actions like `throw` via `ev` just discard the other frames and they will lead to memory leaks and other maybe unexpected behavior. Phpdbg shouldn't crash, though.

info
----

There are multiple informations you can get via info. For that have a look at the `help` command. It tells you what the command does and what subcommands exist.

    > help info
    Command: info  Alias: i  displays some informations

    info commands provide quick access to various types of information about the PHP environment
    By default general information about environment and PHP build is shown.
    Specific info commands are show below:
    
      Target   Alias  Purpose
      break      b      show current breakpoints
      files      F      show included files
      classes    c      show loaded classes
      funcs      f      show loaded functions
      error      e      show last error
      constants  d      show user-defined constants
      vars       v      show active variables
      globals    g      show superglobal variables
      literal    l      show active literal constants
      memory     m      show memory manager stats

Go ahead and play a bit with have you all can do. Just `help` and then look what (sub)commands exist.
