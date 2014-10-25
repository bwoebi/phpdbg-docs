Until now we just were able to inspect our environment on fatal errors or script end.
That is what breakpoints are for:

Breakpoints stop execution on what you specified them to break and return control to you. Then you can inspect your current environment.

If you want to stop at a specific line, you just write

    break 10

That will add a breakpoint in the current file being executed on the sepcified line, in this case on line 10.

Let us start an example debugging session on the file a.php. We want this file below to output `beginning of minute` in the first 30 seconds, then `end of minute` in the last 30 seconds.

    <?php
    function mode ($m) {
        if ($m == 0) {
            return "beginning";
        } else {
            return "end";
        }
    }
    
    $second = time() % 60;
    $mode = mode(round($second / 30)); // line 11

    print "$mode of minute";
    ?>
    
But, we seem to get only "beginning" for the first 15 seconds. That is not what we expected!

We maybe should break before the call to the function `mode` to see what the value of `$second` is.

Then start a simple debugger session:

    phpdbg a.php
    prompt> b 11
    [Breakpoint #0 added at /Users/Bob/php-src-5.6/a.php:11]
    prompt> r
    [Breakpoint #0 at /Users/Bob/php-src-5.6/a.php:11, hits: 1]
    >00011:     $mode = mode(round($second / 30));
     00012: 
     00013:     print "$mode of minute";
    prompt> ev $second
    20
     
So far, correct, `$second` is between 16 and 29, now, let us inspect what we get passed inside `mode` function. `Step` a bit forward, so that we can inspect the value of `$m`. `Step` means that we continue execution of the script until we reach the next line. In this case, we step twice forward until the body of the function — until `$m` has been fetched.

    prompt> step
    [L11         0x101527ac8 ZEND_SEND_VAL                  @0                   <unused>             <unused>             /a.php]
    [L11         0x101527af8 ZEND_DO_FCALL                  C4                   <unused>             @1                   /a.php]
    [L11         0x101527b28 ZEND_SEND_VAR_NO_REF           @1                   <unused>             <unused>             /a.php]
    [L11         0x101527b58 ZEND_DO_FCALL                  C5                   <unused>             @2                   /a.php]
    [L2          0x101498bf8 ZEND_RECV                      <unused>             <unused>             $m                   /a.php]
    >00002:     function mode ($m) {
     00003:         if ($m == 0) {
     00004:             return "beginning";
    prompt> step
    [L3          0x101498c28 ZEND_IS_EQUAL                  $m                   C0                   @0                   /a.php]
    >00003:         if ($m == 0) {
     00004:             return "beginning";
     00005:         } else {
    prompt> ev $m
    1

Oh, wait. The value is `1`? We expected `0` for `round($second / 30)` when `$second` is `20`. Something is wrong there when passing the function parameter. Seems to be we have used `round` instead of `floor`.

Let me try emulating it like as if we had passed `floor($second / 30)`:

    prompt> ev $m = floor(20 / 30)
    0

Fine, `$m` is now `0`. Now everything should work again. Remove the breakpoint (so that we will not hit it again) with `break del 0` - the `0` being the breakpoint id here. Look above:

    [Breakpoint #0 added at /Users/Bob/php-src-5.6/a.php:11]

`#0` denotes the breakpoint id.

    prompt> break del 0
    [Deleted breakpoint #0]

Finally, just run the code until it ends, with `continue`. It should print now `beginning of minute` because `$m` is now `0`.

    prompt> c
    beginning of minute
    [Script ended normally]

Great, everything works now like expected... Now going to change the code in my file and the world is nice again.

But wait. In the example is `c`, not `continue`? Nearly every commmand has a shortcut for faster working in the debugger. Or do you really always want to write so many characters per command?

A quick list of commands we know so far:

<table>
    <thead>
        <tr><th>Command</th><th>Shortcut</th><th>Action</th></tr>
    </thead>
    <tbody>
        <tr><td>run</td><td>r</td><td>Starts execution of the script</td></tr>
        <tr><td>ev</td><td>&mdash;</td><td>Evaluates an expression</td></tr>
        <tr><td>break</td><td>b</td><td>Sets a breakpoint</td></tr>
        <tr><td>break del</td><td>b d</td><td>Deletes a breakpoint by id</td></tr>
        <tr><td>continue</td><td>c</td><td>Continues code execution until next breakpoint</td></tr>
    </tbody>
</table>
