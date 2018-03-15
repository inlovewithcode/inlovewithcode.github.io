---
author: guidedmissile
comments: false
date: 2017-11-21 14:46:56+00:00
layout: page
link: https://inlovewithcode.wordpress.com/rabbitmq-pika/
slug: rabbitmq-pika
title: RabbitMQ - Pika
wordpress_id: 2583
---

# Short Tutorial on Rabbit MQM & PIKA



To tell you short Rabbit MQM is somewhat a Mail Server. If you still dont understand it, then think of it like a friend who safe keep the courier sent you when you are not available in office.

Technicall speaking, Rabbit is (1) an Open Source (2) Message Queue Broker.



## Tutorial



MQM Definitions:





  * Producer: one who creates a job request.


  * Consumer: one who processer a job request.


  * Queue: one who stores request.


  * Exchange: Gate/Door for Queue.


  * RoutingKey: Key for accessing Queue via Exchange.



Generally, this is how people/process send work


    
    <code>producer -&gt; consumer
    </code>



In Reality, as consumers are not always standing for your instruction, so,.. having a queue system helps


    
    <code>producer -&gt; stack/queue -&gt; consumer
    </code>



For some reasons, mostly a producer generally does not stick to one type of customer and starts creating multiple kind of products for different purposes and consumer


    
    <code>producer -&gt; exchange_server -&gt; Queue -&gt; consumer
    </code>



An **Exchange Server**, understand the producer and sends the requests to relavant queues.



#### Queue



I'm using macbook(good/bad), so here are my installation instructions


    
    <code># Installing RabbitMQ
    brew install rabbitmq
    </code>



Rabbit uses `erlang`, so brew will install it. No need to specify special instruction.



#### Consumer



Now that we have a message broker/message queue manager, we need some body who will actually pick and do that tasks.


    
    <code># pip install celery
    </code>





#### Producer



We will `celery` module itself to create and send work.



## Plan







  1. Created a simple example of a slow running job.


  2. create a queue


  3. created an exchange





### 1. Sample Working Python Program



[code lang=Python]
import random
import time

def fibo(t):
    """Return the smallest fibonaci number less than given value."""
    a = 0
    b = 1
    while (b < t):
        a, b = b, a + b
    return a

def main(value):
    time.sleep(random.random() * 3)
    return fibo(value)
[/code]

Testing fibo


    
    <code>&gt;&gt;&gt; ## testing
    &gt;&gt;&gt; fibo(12), fibo(21), fibo(1112)
    (8, 13, 987)
    </code>



Testing Producer


    
    <code>## testing
    main(12), main(21), main(1112)
    (8, 13, 987)
    </code>





### 2. Working RabbitMq



Experimental Commands


    
    <code>###################################################################
    # rabbit mqm is a Message queue broker
    #    It has Queues, Exchanges for Queues and
    #           Routing Key that connect them.
    #
    #  Here are some commands to reset your MQM if wish to experiment
    ###################################################################
    
    # starting mqm server
    #     webpage     (http://localhost:15672/#/)
    #     credentials (guest/guest)
    rabbitmq-server
    
    # to stop - stopping above does not always kill the background
    #   so use this command.
    kill `ps -eaf | grep -v grep | grep rabbit | awk '{ print $2 }'`
    
    ###################################################################
    # rabbit mqm - resetting queues
    ###################################################################
    
    # stop application
    rabbitmqctl stop_app
    
    # reset
    rabbitmqctl reset
    
    # start
    rabbitmqctl start_app
    
    # kill rabbit 
    kill `ps -eaf | grep -v grep | grep rabbit | awk '{ print $2 }'`
    
    ###################################################################
    </code>



If you have installed correct, you can run following command in your terminal


    
    <code>rabbitmq-server
    </code>



The default rabbitmq server comes with a UI, and you can find it at following url.





  * [http://localhost:15672/#/](http://localhost:15672/#/)



Default credentials are username: `guest` and password: `guest`



#### 1. created queues, exchanges and routing_keys







  * Go to [http://localhost:15672/#/queues](http://localhost:15672/#/queues)


  * Create a queue name as `test-queue1`, with no extra but default params


  * Create a queue name as `test-queue2`, like above


  * Go to [http://localhost:15672/#/exchanges](http://localhost:15672/#/queues) with name as `test-exchange` and type as `direct`.



In exchange page, you can see the newly created `test-exchange` in the list of exchanges, click it.

Go to section, `Add binding from this exchange` and start adding following





  * `To queue`, `test-queue1` and routing key is `redpill`


  * `To queue`, `test-queue2` and routing key is `bluepill`





## Let's learn to send a request to a queue



Following shell code``

[code lang=bash]
SDS-bash3.2$ cat create_request.py
from tasks import wrapped_main

if __name__ == "__main__":
    print(wrapped_main.delay(15))
[/code]

Executing above code

[code lang=bash]
SDS-bash3.2$ python create_request.py
94c77870-2262-4ccd-af22-b45326c3c920
[/code]

In Rabbit MQM, we can see a message came to `Celery` from **Queues** Page.



<blockquote>
  Issue is, we need this message to our `test-queue1`.
</blockquote>



[code lang=bash]
# taking a backup copy
SDS-bash3.2$ cp -p tasks.py  tasks_old.py

# update the file
SDS-bash3.2$ vi tasks_old.py

# check the differences
SDS-bash3.2$ diff tasks.py  tasks_old.py
8c8
< @app.task(queue='test-queue1')
---
> @app.task
[/code]

In Rabbit MQM, we can see a message came to `test-queue1` from **Queues** Page.



<blockquote>
  Next Issue, we need to see this output message.
</blockquote>



[code lang=text]
SDS-bash3.2$ cat tasks.py
# tasks.py

from celery import Celery
from kombu import Exchange, Queue
from main import main

pika_cred = pika.PlainCredentials('guest', 'guest')
pika_conn_params = pika.ConnectionParameters('localhost', credentials=pika_cred)
pika_connection = pika.BlockingConnection(pika_conn_params)
channel = pika_connection.channel()


######################################################################

# creating architecture - queues
channel.queue_declare(queue='test-queue1')
channel.queue_declare(queue='test-queue2')

# creating architecture - queues
channel.exchange_declare(exchange='test-exchange', exchange_type='direct')

# creating architecture - queues
channel.queue_bind(exchange='test-exchange', queue='test-queue1', routing_key='redpill')
channel.queue_bind(exchange='test-exchange', queue='test-queue2', routing_key='bluepill')

######################################################################

app = Celery("tasks", broker="pyamqp://guest@localhost//")

@app.task(queue='test-queue1')
def wrapped_main(value):
    return main(value)
[/code]

Adding a backend process now.

[code lang=text]
<br />def pika_messager(message):
    """A messenger to send message to Queue."""
    header = "Host: " + str(os.uname()[1]) + "\tDatetime: " + str(time.ctime()) + '\n\n'
    print('start Pika Connection ' + header)
    pika_connection = pika.BlockingConnection(pika_conn_params)
    channel = pika_connection.channel()
    channel.basic_publish(exchange='variantCallerExchange', routing_key='variantCallerRoutingKey', body=header+message)
    channel.close()
    pika_connection.close()
    print('Pika Connection is close now')


@app.task(queue='test-queue1')
def wrapped_main(value):
    result = main(value)
    pika_messager("Job finished ! Result is" + result)
    return result

[/code]



## Complete Code & Summary



We have a `main.py` which our main script(product) which can do a certain job. We are usinga RabbitMq, a message queue manager(broker) to manage requests. We will use `pika` for creating requests, creating message(queues, exchanges, routing keys) and we will use `celery` for reporting completed jobs.

**Note:** Complete jobs means both success or failure.

A



<blockquote>
  filename: main.py
</blockquote>



[code lang=python]
#! main.py
import random
import time

def fibo(t):
    """Return the smallest fibonaci number less than given value."""
    a = 0
    b = 1
    while (b < t):
        a, b = b, a + b
    return a

def main(value):
    time.sleep(random.random() * 10)
    return fibo(value)
[/code]



<blockquote>
  filename: task.py
</blockquote>



[code lang=python]
from celery import Celery
from kombu import Exchange, Queue
from main import main

pika_cred = pika.PlainCredentials('guest', 'guest')
pika_conn_params = pika.ConnectionParameters('localhost', credentials=pika_cred)
pika_connection = pika.BlockingConnection(pika_conn_params)
channel = pika_connection.channel()


######################################################################

# creating architecture - queues
channel.queue_declare(queue='test-queue1')
channel.queue_declare(queue='test-queue2')

# creating architecture - queues
channel.exchange_declare(exchange='test-exchange', exchange_type='direct')

# creating architecture - queues
channel.queue_bind(exchange='test-exchange', queue='test-queue1', routing_key='redpill')
channel.queue_bind(exchange='test-exchange', queue='test-queue2', routing_key='bluepill')

######################################################################

app = Celery("tasks", broker="pyamqp://guest@localhost//")

def pika_messager(message):
    """A messenger to send message to Queue."""
    header = "Host: " + str(os.uname()[1]) + "\tDatetime: " + str(time.ctime()) + '\n\n'
    print('start Pika Connection ' + header)
    pika_connection = pika.BlockingConnection(pika_conn_params)
    channel = pika_connection.channel()
    channel.basic_publish(exchange='variantCallerExchange', routing_key='variantCallerRoutingKey', body=header+message)
    channel.close()
    pika_connection.close()
    print('Pika Connection is close now')


@app.task(queue='test-queue1')
def wrapped_main(value):
    result = main(value)
    pika_messager("Job finished ! Result is" + result)
    return result

[/code]



# Testing



[code lang=python]
import os
import time
import pika

# Pika - result messages
pika_cred = pika.PlainCredentials('guest', 'guest')
pika_conn_params = pika.ConnectionParameters('localhost', credentials=pika_cred)

pika_connection = pika.BlockingConnection(pika_conn_params)
channel = pika_connection.channel()
pika_connection = pika.BlockingConnection(pika_conn_params)
channel.queue_declare(queue='test-queue1')

######################################################################
# sending messages
header = "Host: " + str(os.uname()[1]) + "\tDatetime: " + str(time.ctime()) + '\n\n'
channel.basic_publish(exchange='test-exchange', routing_key='bluepill', body=header + message)
######################################################################
[/code]
