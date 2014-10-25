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

Then each step command will just advance until the next opcode - instead of the next line.

To reset it later to line-by-line stepping:

    s s line

leave
=====

...

finish
======

....

until
=====

.....
