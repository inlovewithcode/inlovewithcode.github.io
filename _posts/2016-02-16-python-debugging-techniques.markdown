---
author: guidedmissile
comments: false
date: 2016-02-16 07:29:20+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2016/02/16/python-debugging-techniques/
slug: python-debugging-techniques
title: Python Debugging Techniques
wordpress_id: 635
categories:
- Python
---

## Python Debugging Techniques












This article covers several techniques for debugging Python programs. The applicability of these techniques ranges from simple scripts to complex applications. The topics that are covered include launching an interactive console from within your program, using the Python debugger, and implementing robust logging. Various tips are included along the way to help you debug and fix problems quickly and efficiently.






	
  * Launching an interactive console with code.interact()

	
    * [Using the Python Debugger](http://web.archive.org/web/20120819135307/http://aymanh.com/python-debugging-techniques#using-the-python-debugger)

	
      * [Stepping through program execution](http://web.archive.org/web/20120819135307/http://aymanh.com/python-debugging-techniques#stepping-through-program-execution)

	
        * [Setting breakpoints](http://web.archive.org/web/20120819135307/http://aymanh.com/python-debugging-techniques#setting-breakpoints)

	
        * [The best pdb tip](http://web.archive.org/web/20120819135307/http://aymanh.com/python-debugging-techniques#the-best-pdb-tip)

	
        * [Summary of pdb commands and short forms](http://web.archive.org/web/20120819135307/http://aymanh.com/python-debugging-techniques#summary-of-pdb-commands-and-short-forms)




	
      * [Logging](http://web.archive.org/web/20120819135307/http://aymanh.com/python-debugging-techniques#logging)

	
        * [Logging to a file and adding date/time](http://web.archive.org/web/20120819135307/http://aymanh.com/python-debugging-techniques#logging-to-a-file-and-adding-datetime)

	
        * [Logging levels](http://web.archive.org/web/20120819135307/http://aymanh.com/python-debugging-techniques#logging-levels)

	
        * [Convenient template for logging](http://web.archive.org/web/20120819135307/http://aymanh.com/python-debugging-techniques#convenient-template-for-logging)
















### Launching an interactive console with code.interact()


The Python interactive console is an awesome tool for experimenting with Python code. It provides a read-eval-print loop that allows you to experiment with Python code easily and quickly, without having to write and run a complete program. Wouldn't be convenient if you could use the same technique to debug an existing program? Fortunately, this is already possible thanks to the [`code`](http://web.archive.org/web/20120819135307/http://docs.python.org/library/code.html) module. This module has a function called [`interact()`](http://web.archive.org/web/20120819135307/http://docs.python.org/library/code.html#code.interact) that stops execution and gives you an interactive console to examine the current state of your program. To use this function, simply embed the following at the line were you want the console to start:




    
    <span class="kn">import</span> <span class="nn">code</span><span class="p">;</span> <span class="n">code</span><span class="o">.</span><span class="n">interact</span><span class="p">(</span><span class="n">local</span><span class="o">=</span><span class="nb">locals</span><span class="p">())</span>
    





The resulting console inherits the local scope of the line on which `code.interact()` is called. This enables you to check the current state of your program to understand its behavior and make any necessary corrections.

To exit the interactive console and continue with the execution of your program, press `Ctrl+D` in Unix/Linux systems, or `Ctrl+Z` in Windows. Alternatively, you can type `exit()` in the console and hit enter to exit the console and abort your program.


### Using the Python Debugger


When you need to examine the execution flow of your program, an interactive console is not going to be enough. For situations like this, you can use the [Python debugger](http://web.archive.org/web/20120819135307/http://docs.python.org/library/pdb.html). It provides a full-fledged debugging environment that supports breakpoints, stepping through source code, stack inspection and much more. This debugger comes with the standard python distribution as a module named `pdb`.

To learn how to use `pdb`, let's write a simple program that calculates the first 10 [Fibonacci numbers](http://web.archive.org/web/20120819135307/http://en.wikipedia.org/wiki/Fibonacci_number):




    
    <span class="k">def</span> <span class="nf">main</span><span class="p">():</span>
      <span class="n">low</span><span class="p">,</span> <span class="n">high</span> <span class="o">=</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">1</span>
      <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">xrange</span><span class="p">(</span><span class="mi">10</span><span class="p">):</span>
        <span class="k">print</span> <span class="n">high</span>
        <span class="n">low</span><span class="p">,</span> <span class="n">high</span> <span class="o">=</span> <span class="n">high</span><span class="p">,</span> <span class="n">low</span> <span class="o">+</span> <span class="n">high</span>
    
    <span class="k">if</span> <span class="n">__name__</span> <span class="o">==</span> <span class="s">'__main__'</span><span class="p">:</span>
      <span class="n">main</span><span class="p">()</span>
    





Assuming that the file name is `fib.py`, we can run the program in `pdb` using the following command:




    
    <span class="nv">$ </span>python -m pdb fib.py
    





The command results in the following output:




    
    <span class="o">></span> <span class="n">fib</span><span class="o">.</span><span class="n">py</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span><span class="o"><</span><span class="n">module</span><span class="o">></span><span class="p">()</span>
    <span class="o">-></span> <span class="k">def</span> <span class="nf">main</span><span class="p">():</span>
    <span class="p">(</span><span class="n">Pdb</span><span class="p">)</span>
    





The first line of output contains the current module name, line number and function name (function name currently appears as `<module>()` because we are still at module level). The second line of output contains the current line of source code that is being executed. `pdb` also provides an interactive console to debug the program. This console is different from the familiar Python console. You can see its commands by typing `help` and hitting enter. Also, typing`help <command>` gives you help on the command you provided. Let's learn about these commands.


#### Stepping through program execution


The `list` command prints a few lines of context around the current line. Let's give it a try:




    
    <span class="p">(</span><span class="n">Pdb</span><span class="p">)</span> <span class="nb">list</span>
      <span class="mi">1</span>  <span class="o">-></span> <span class="k">def</span> <span class="nf">main</span><span class="p">():</span>
      <span class="mi">2</span>       <span class="n">low</span><span class="p">,</span> <span class="n">high</span> <span class="o">=</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">1</span>
      <span class="mi">3</span>       <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">xrange</span><span class="p">(</span><span class="mi">10</span><span class="p">):</span>
      <span class="mi">4</span>         <span class="k">print</span> <span class="n">high</span>
      <span class="mi">5</span>         <span class="n">low</span><span class="p">,</span> <span class="n">high</span> <span class="o">=</span> <span class="n">high</span><span class="p">,</span> <span class="n">low</span> <span class="o">+</span> <span class="n">high</span>
      <span class="mi">6</span>  
      <span class="mi">7</span>     <span class="k">if</span> <span class="n">__name__</span> <span class="o">==</span> <span class="s">'__main__'</span><span class="p">:</span>
      <span class="mi">8</span>       <span class="n">main</span><span class="p">()</span>
    <span class="p">[</span><span class="n">EOF</span><span class="p">]</span>
    





Next, let's step through our program. The `next` command executes the current line and moves next.




    
    <span class="p">(</span><span class="n">Pdb</span><span class="p">)</span> <span class="nb">next</span>
    <span class="o">></span> <span class="n">fib</span><span class="o">.</span><span class="n">py</span><span class="p">(</span><span class="mi">7</span><span class="p">)</span><span class="o"><</span><span class="n">module</span><span class="o">></span><span class="p">()</span>
    <span class="o">-></span> <span class="k">if</span> <span class="n">__name__</span> <span class="o">==</span> <span class="s">'__main__'</span><span class="p">:</span>
    





At this point, the `main()` function has been defined, but not called. This is why the execution has jumped to the `if`condition on line 7. Let's call `next` again:




    
    <span class="p">(</span><span class="n">Pdb</span><span class="p">)</span> <span class="n">n</span>
    <span class="o">></span> <span class="n">fib</span><span class="o">.</span><span class="n">py</span><span class="p">(</span><span class="mi">8</span><span class="p">)</span><span class="o"><</span><span class="n">module</span><span class="o">></span><span class="p">()</span>
    <span class="o">-></span> <span class="n">main</span><span class="p">()</span>
    





We are now about to call the `main()` function. Running `next` at this point will call `main()` and move to the next line. Since we are at the end of the file, this means that the program will finish executing. But we don't want this; we want to step into the `main()` function. To do this, we use the `step` command:




    
    <span class="p">(</span><span class="n">Pdb</span><span class="p">)</span> <span class="n">step</span>
    <span class="o">--</span><span class="n">Call</span><span class="o">--</span>
    <span class="o">></span> <span class="n">fib</span><span class="o">.</span><span class="n">py</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span><span class="n">main</span><span class="p">()</span>
    <span class="o">-></span> <span class="k">def</span> <span class="nf">main</span><span class="p">():</span>
    





From here, you can continue calling `next` to step through the `main()`. If at some point you want to examine the value of a variable, you can use the `pp` command (short for pretty-print):




    
    <span class="p">(</span><span class="n">Pdb</span><span class="p">)</span> <span class="n">pp</span> <span class="n">high</span>
    <span class="mi">2</span>
    





If you are done with examining the `main()` function, you can either use the `continue` command, which exits the debugging console and continues the execution of the program, or use the `return`, which continues the execution until the current function returns. Alternatively, you can stop the execution altogether and abort by using the `exit`command.


#### Setting breakpoints


Next, we will learn about breakpoints. More often than not, you want to invoke the debugger at a particular function or line number, rather than step through the execution of the whole program. To do so, you can set a breakpoint and continue the execution of the program. When the breakpoint is reached, the debugger is invoked.

To set a breakpoint, use the `break` command. It takes a file name and line number or function name. To break at line 4 in fib.py, use:




    
    <span class="p">(</span><span class="n">Pdb</span><span class="p">)</span> <span class="k">break</span> <span class="n">fib</span><span class="o">.</span><span class="n">py</span><span class="p">:</span><span class="mi">4</span>
    





To break when the `main()` function is called, use:




    
    <span class="p">(</span><span class="n">Pdb</span><span class="p">)</span> <span class="k">break</span> <span class="n">fib</span><span class="o">.</span><span class="n">main</span>
    





Furthermore, you can attach a condition to the breakpoint. Execution breaks only if this condition is `True`. For example, to break at line 4 in fib.py when `high` is greater than 10, use:




    
    <span class="p">(</span><span class="n">Pdb</span><span class="p">)</span> <span class="k">break</span> <span class="n">fib</span><span class="o">.</span><span class="n">py</span><span class="p">:</span><span class="mi">4</span><span class="p">,</span> <span class="n">high</span> <span class="o">></span> <span class="mi">10</span>
    







#### The best pdb tip


Now it's time for my favorite feature in `pdb`. It you put the following snippet somewhere in your program and run it normally, execution will stop and a debugging session will start when this line is reached:




    
    <span class="kn">import</span> <span class="nn">pdb</span><span class="p">;</span> <span class="n">pdb</span><span class="o">.</span><span class="n">set_trace</span><span class="p">()</span>
    





This approach is very convenient because it does not require launching your program in a special way or remembering to set breakpoints. You simply add the line above and start the program normally, and the debugger will be invoked exactly where you want. In practice, I think you will use this snippet to start `pdb` most of the time.


#### Summary of pdb commands and short forms


Finally, `pdb` commands have short forms. The following table summarizes the commands presented in this section, and their short forms:
<table >

<tr >
Command
Short form
Description
</tr>

<tbody >
<tr >

<td >break
</td>

<td >b
</td>

<td >Set a breakpoint.
</td>
</tr>
<tr >

<td >continue
</td>

<td >c
</td>

<td >Continue with program execution.
</td>
</tr>
<tr >

<td >exit
</td>

<td >q
</td>

<td >Abort the program.
</td>
</tr>
<tr >

<td >help
</td>

<td >h
</td>

<td >Print list of commands or help for a given command.
</td>
</tr>
<tr >

<td >list
</td>

<td >l
</td>

<td >Show source code around current line.
</td>
</tr>
<tr >

<td >return
</td>

<td >r
</td>

<td >Continue execution until the current function returns.
</td>
</tr>
</tbody>
</table>


### Logging


A primitive way of debugging programs is to embed `print` statements through out the code to track execution flow and state. However, this approach can quickly become unmaintainable for a number of reasons:



	
  * Normal program output is mixed with debugging output. This makes it difficult to distinguish between the two.

	
  * There is no easy way to disable debugging output, or redirect it to a file.

	
  * When done with debugging, it may be difficult to track down and remove all `print` statements that are scattered over the code.


Python provides an alternative to debug `print` statements that doesn't suffer from the shortcomings above. This alternative comes in the form of a module called [`logging`](http://web.archive.org/web/20120819135307/http://docs.python.org/library/logging.html), and it is very powerful and easy to use.

Let's start with a simple example. The following snippet imports the `logging` module and sets the logging level to debug:




    
    <span class="kn">import</span> <span class="nn">logging</span>
    
    <span class="n">logging</span><span class="o">.</span><span class="n">basicConfig</span><span class="p">(</span><span class="n">level</span><span class="o">=</span><span class="n">logging</span><span class="o">.</span><span class="n">DEBUG</span><span class="p">)</span>
    





The call to `logging.basicConfig()` should be done once when your program starts. Now, whenever you want to print a debug message, call `logging.debug()`:




    
    <span class="n">logging</span><span class="o">.</span><span class="n">debug</span><span class="p">(</span><span class="s">'This is a debug message.'</span><span class="p">)</span>
    





This will send the following string to `stderr`:




    
    <span class="err">DEBUG:root:This</span> <span class="err">is</span> <span class="err">a</span> <span class="err">debugging</span> <span class="err">message.</span>
    





`DEBUG` indicates that this is a debug message. `root` indicates that this is the root logger, as it is possible to have multiple loggers (don't worry about this for now).

Now we have a better logging system that can be globally switched on and off. To turn off debug messages, simply omit the `level` argument when calling `logging.basicConfig()`:




    
    <span class="n">logging</span><span class="o">.</span><span class="n">basicConfig</span><span class="p">()</span>
    







#### Logging to a file and adding date/time


To take full advantage of the `logging` module, let's have a look at some of the options that can be provided to`logging.basicConfig()`:
<table >

<tr >
Argument
Description
</tr>

<tbody >
<tr >

<td >filename
</td>

<td >Send log messages to a file.
</td>
</tr>
<tr >

<td >filemode
</td>

<td >The mode to open the file in (defaults to `'a'`).
</td>
</tr>
<tr >

<td >format
</td>

<td >The format of log messages.
</td>
</tr>
<tr >

<td >dateformat
</td>

<td >date/time format in log messages.
</td>
</tr>
<tr >

<td >level
</td>

<td >Level of messages to be printed (more on this later).
</td>
</tr>
</tbody>
</table>
For example, to configure the logging module to send debug messages to a file called `debug.log`, use:




    
    <span class="n">logging</span><span class="o">.</span><span class="n">basicConfig</span><span class="p">(</span><span class="n">level</span><span class="o">=</span><span class="n">logging</span><span class="o">.</span><span class="n">DEBUG</span><span class="p">,</span> <span class="n">filename</span><span class="o">=</span><span class="s">'debug.log'</span><span class="p">)</span>
    





Log messages will be appended to `debug.log` if the file already exists. This means that your log messages will be kept even if you run your program multiple times.

To add date/time to your log messages, use:




    
    <span class="n">logging</span><span class="o">.</span><span class="n">basicConfig</span><span class="p">(</span><span class="n">level</span><span class="o">=</span><span class="n">logging</span><span class="o">.</span><span class="n">DEBUG</span><span class="p">,</span> <span class="n">filename</span><span class="o">=</span><span class="s">'debug.log'</span><span class="p">,</span>
                        <span class="n">format</span><span class="o">=</span><span class="s">'</span><span class="si">%(asctime)s</span> <span class="si">%(levelname)s</span><span class="s">: </span><span class="si">%(message)s</span><span class="s">'</span><span class="p">,</span>
                        <span class="n">datefmt</span><span class="o">=</span><span class="s">'%Y-%m-</span><span class="si">%d</span><span class="s"> %H:%M:%S'</span><span class="p">)</span>
    





This will result in log messages like the following:




    
    <span class="mi">2009</span><span class="o">-</span><span class="mi">08</span><span class="o">-</span><span class="mi">30</span> <span class="mi">23</span><span class="p">:</span><span class="mi">30</span><span class="p">:</span><span class="mi">49</span> <span class="n">DEBUG:</span> <span class="n">This</span> <span class="n">is</span> <span class="n">a</span> <span class="n">debug</span> <span class="n">message</span><span class="o">.</span>
    







#### Logging levels


The `logging` supports multiple levels of log messages in addition to `DEBUG`. Here is the full list:
<table >

<tr >
Level
Function
</tr>

<tbody >
<tr >

<td >logging.CRITICAL
</td>

<td >logging.critical()
</td>
</tr>
<tr >

<td >logging.ERROR
</td>

<td >logging.error()
</td>
</tr>
<tr >

<td >logging.WARNING
</td>

<td >logging.warning()
</td>
</tr>
<tr >

<td >logging.INFO
</td>

<td >logging.info()
</td>
</tr>
<tr >

<td >logging.DEBUG
</td>

<td >logging.debug()
</td>
</tr>
</tbody>
</table>
Setting the logging level to a value enables log messages for this level and all levels above it. So if you set the level to`logging.WARNING`, you will get `WARNING`, `ERROR` and `CRITICAL` messages. This allows you to have different levels of log verbosity.


#### Convenient template for logging


Before I conclude this section, I will provide a simple template for enabling logging functionality in your programs. This template uses command-line flags to change the level logging, which is more convenient that modifying source code.




    
    <span class="kn">import</span> <span class="nn">logging</span>
    <span class="kn">import</span> <span class="nn">optparse</span>
    
    <span class="n">LOGGING_LEVELS</span> <span class="o">=</span> <span class="p">{</span><span class="s">'critical'</span><span class="p">:</span> <span class="n">logging</span><span class="o">.</span><span class="n">CRITICAL</span><span class="p">,</span>
                      <span class="s">'error'</span><span class="p">:</span> <span class="n">logging</span><span class="o">.</span><span class="n">ERROR</span><span class="p">,</span>
                      <span class="s">'warning'</span><span class="p">:</span> <span class="n">logging</span><span class="o">.</span><span class="n">WARNING</span><span class="p">,</span>
                      <span class="s">'info'</span><span class="p">:</span> <span class="n">logging</span><span class="o">.</span><span class="n">INFO</span><span class="p">,</span>
                      <span class="s">'debug'</span><span class="p">:</span> <span class="n">logging</span><span class="o">.</span><span class="n">DEBUG</span><span class="p">}</span>
    
    <span class="k">def</span> <span class="nf">main</span><span class="p">():</span>
      <span class="n">parser</span> <span class="o">=</span> <span class="n">optparse</span><span class="o">.</span><span class="n">OptionParser</span><span class="p">()</span>
      <span class="n">parser</span><span class="o">.</span><span class="n">add_option</span><span class="p">(</span><span class="s">'-l'</span><span class="p">,</span> <span class="s">'--logging-level'</span><span class="p">,</span> <span class="n">help</span><span class="o">=</span><span class="s">'Logging level'</span><span class="p">)</span>
      <span class="n">parser</span><span class="o">.</span><span class="n">add_option</span><span class="p">(</span><span class="s">'-f'</span><span class="p">,</span> <span class="s">'--logging-file'</span><span class="p">,</span> <span class="n">help</span><span class="o">=</span><span class="s">'Logging file name'</span><span class="p">)</span>
      <span class="p">(</span><span class="n">options</span><span class="p">,</span> <span class="n">args</span><span class="p">)</span> <span class="o">=</span> <span class="n">parser</span><span class="o">.</span><span class="n">parse_args</span><span class="p">()</span>
      <span class="n">logging_level</span> <span class="o">=</span> <span class="n">LOGGING_LEVELS</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="n">options</span><span class="o">.</span><span class="n">logging_level</span><span class="p">,</span> <span class="n">logging</span><span class="o">.</span><span class="n">NOTSET</span><span class="p">)</span>
      <span class="n">logging</span><span class="o">.</span><span class="n">basicConfig</span><span class="p">(</span><span class="n">level</span><span class="o">=</span><span class="n">logging_level</span><span class="p">,</span> <span class="n">filename</span><span class="o">=</span><span class="n">options</span><span class="o">.</span><span class="n">logging_file</span><span class="p">,</span>
                          <span class="n">format</span><span class="o">=</span><span class="s">'</span><span class="si">%(asctime)s</span> <span class="si">%(levelname)s</span><span class="s">: </span><span class="si">%(message)s</span><span class="s">'</span><span class="p">,</span>
                          <span class="n">datefmt</span><span class="o">=</span><span class="s">'%Y-%m-</span><span class="si">%d</span><span class="s"> %H:%M:%S'</span><span class="p">)</span>
    
      <span class="c"># Your program goes here.</span>
      <span class="c"># You can access command-line arguments using the args variable.</span>
    
    <span class="k">if</span> <span class="n">__name__</span> <span class="o">==</span> <span class="s">'__main__'</span><span class="p">:</span>
      <span class="n">main</span><span class="p">()</span>
    





By default, the `logging` module prints critical, error and warning messages. To change this so that all levels are printed, use:




    
    <span class="nv">$ </span>./your-program.py --logging<span class="o">=</span>debug
    





To send log messages to a file called `debug.log`, use:




    
    <span class="nv">$ </span>./your-program.py --logging-level<span class="o">=</span>debug --logging-file<span class="o">=</span>debug.log















