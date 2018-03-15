---
author: guidedmissile
comments: true
date: 2015-08-10 12:41:31+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/08/10/threading-in-python/
slug: threading-in-python
title: Threading in Python
wordpress_id: 539
categories:
- Python
---

_This is a re-blogged post. Find the initial source at the bottom of this page._

Recently in my effort to learn something new in Python, I thought of having a small introduction to threading in python.

The following modules are related to python that come in default installation in python:



	
  * [threading](http://docs.python.org/library/threading.html)

	
  * [thread](http://docs.python.org/library/thread.html)


From Python Docs:


<blockquote>Note

The thread module has been renamed to _thread in Python 3.0. The 2to3 tool will automatically adapt imports when converting your sources to 3.0; however, you should consider using the high-level threading module instead.</blockquote>


Thus, it can be assumed that when developing scripts that may use threading, always use the [threading](http://docs.python.org/library/threading.html) module rather than [thread](http://docs.python.org/library/thread.html).

To save myself some time, it would be better if you can read the basic concepts of threads from [wiki](http://en.wikipedia.org/wiki/Thread_(computer_science)) itself.

Now, comes the first program.

    
    #!/usr/bin/env python
    
    import time
    import thread
    
    def myfunction(string, sleeptime, max_count, *args):
    
        counter = 0
        ## To manage I/O
        time.sleep(0.2)
        while counter < max_count:
            print "{}. {}".format(counter, string)
            counter += 1
            time.sleep(sleeptime)
            #sleep for a specified amount of time.
    
    if __name__=="__main__":
    
        print "thread Started : {}".format(thread.start_new_thread(myfunction,("Thread No:1", 2, 10)))
    ##    thread.exit_thread
    ##
        ## this can be omitted
        while 1:
            pass
    
    


In the above script, a new thread is started using the function myfunction. The arguments to the function are passed to the [start_new_thread()](http://docs.python.org/library/thread.html#thread.start_new_thread) using a [tuple](http://docs.python.org/library/functions.html#tuple) (do remember to make a [tuple](http://docs.python.org/library/functions.html#tuple) from the arguments you want to pass). The [start_new_thread()](http://docs.python.org/library/thread.html#thread.start_new_thread) returns the thread identifier of the thread started (which has been printed here).

A very usual thing I noticed in threaded programs is the use of [time.sleep()](http://docs.python.org/library/time.html#time.sleep), it helps in synchronizing the input output on the terminal. In actual backend scripts, the sleep function would not prove useful (I may be wrong!)

The last example was just for introduction. To jump up the level, let’s calculate the [Fibonacci series](http://en.wikipedia.org/wiki/Fibonacci_sequence) from a thread.

Code:

    
    #Fibonacci threader
    
    import time, thread, threading
    
    def fib(n):
        a, b = 0, 1
        while a</pre>
    &nbsp;
    
    The above script uses both <a title="Python Docs" href="http://docs.python.org/library/thread.html">thread</a> and <a title="Python Docs" href="http://docs.python.org/library/threading.html">threading</a> module. The thread module is used to create threads and threading module is used to get information on the current running threads in the process.
    
    Here the function fib(n) is actually a <a title="Python Docs" href="http://wiki.python.org/moin/Generators">generator</a> and returning a iterator (returning a <a title="Python Docs" href="http://docs.python.org/release/2.5.2/ref/yield.html">generator iterator</a>). Thus we are able to iterate over the Fibonacci numbers using these generators. After the required number of Fibonacci numbers have been generated, <a title="Python Docs" href="http://docs.python.org/library/thread.html#thread.exit">thread.exit_thread() </a>is called which exits the running thread silently.
    
    After creating the thread the script prints the information of the running threads. (Execute to see)
    
    In the end, I would be showing you the code for the (quite famous) <a title="Wikipedia" href="http://en.wikipedia.org/wiki/Producer-consumer_problem">Consumer-Producer problem</a> which would include the code for using locks.
    
    Code:
    
    1
    #!/usr/bin/env python
    
    import time
    import thread
    
    ## Implementing consumer-producer problem using threads and locks
    
    product = []
    
    def producer(lock, produce_time, lim, *args):
    
        pr_val = 0
    
        while True:
    
            print "Producing.."
            time.sleep(produce_time)
            print "Produced {}".format(pr_val)
    
            lock.acquire_lock()
            print "P: Lock ACK"
            product.append(pr_val)
            print "Added product {}".format(pr_val)
            lock.release_lock()
            print "P: Release ACK"
    
            pr_val += 1
    
            if pr_val > lim:
                break
    
    def consumer(lock, consume_time, waiting_time, lim, *args):
    
        con_val = 0
        got_product = False
    
        while True:
    
            lock.acquire_lock()
            print "C: Lock ACK"
    
            try:
                con_val = product.pop()
                print "Retrieved value {}".format(con_val)
                got_product = True
            except IndexError:
                print "No produce!"
                got_product = False
    
            lock.release_lock()
            print "C: Release ACK"
    
            if got_product:
                print "Consuming.. {}".format(con_val)
                time.sleep(consume_time)
            else:
                print "Waiting for produce"
                time.sleep(waiting_time)
    
            if con_val == lim:
                break
    
    if __name__=="__main__":
    
        lock=thread.allocate_lock()
        max_produce = 3
        thread.start_new_thread(producer,(lock, 1, max_produce))
        thread.start_new_thread(consumer,(lock, 2, 1, max_produce))
    
        # Required for commandline output
        while 1:
            pass
    
    


The above code creates a lock to be used by the consumer and producer to acquire the produce-line. Then we define the units to be produced. When the threads are started, the consumer and producer are also told the consume-time and produce-time as arguments (these values are implemented in the program using the [time.sleep()](http://docs.python.org/library/time.html#time.sleep) function).

The consumer thread starts with acquiring the lock on the produce-line and then taking the product from it. If there is no produce yet, it prints an error message. Else, the produce is picked and the lock released. The consumer then consumes the produce and go backs to the start of the loop.

The producer thread starts by producing an item. Then it acquires the lock on the produce-line and adds the produce to it. Then it releases the lock and starts reproducing.

What I have not covered: The threads can also be created and defined using classes. I could not cover that in this post. A good resource of it can be from [IBM](http://www.ibm.com/developerworks/aix/library/au-threadingpython/) and [devshed](http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/).

Github repository for it : [https://github.com/ayushgoel/PythonScripts/tree/master/learning_threading](https://github.com/ayushgoel/PythonScripts/tree/master/learning_threading)

Also, python (CPython actually) is known to be not very good at threading because of GIL (Global Interpreter Lock) on all the data. Google for more information. :P

_Source: [https://techmyway.wordpress.com/2012/04/15/threading-in-python-theory-implementation-and-code/](https://techmyway.wordpress.com/2012/04/15/threading-in-python-theory-implementation-and-code/)_
