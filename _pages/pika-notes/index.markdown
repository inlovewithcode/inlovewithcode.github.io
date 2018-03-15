---
author: guidedmissile
comments: false
date: 2017-11-21 13:37:08+00:00
layout: page
link: https://inlovewithcode.wordpress.com/pika-notes/
slug: pika-notes
title: RabbitMQ - Pika Notes
wordpress_id: 2574
---

### Pika Tutorial



Hoping that you already have RabbitMq server up and running on your local system, we have created this tutorial.

[code lang="python"]
import pika
[/code]

[code lang="python"]
pika_cred = pika.PlainCredentials('guest', 'guest')
pika_conn_params = pika.ConnectionParameters('localhost', credentials=pika_cred)

pika_connection = pika.BlockingConnection(pika_conn_params)
channel = pika_connection.channel()
[/code]



### Declaring Queues



[code lang="python"]
channel.queue_declare(queue='test-queue1')
[/code]

[code lang="python"]
channel.queue_declare(queue='test-queue2')
[/code]



### Declaring Exchanges



[code lang="python"]
channel.exchange_declare(exchange='test-exchange', exchange_type='direct')
[/code]



### Declaring RoutingKey



[code lang="python"]
channel.queue_bind(exchange='test-exchange', queue='test-queue1', routing_key='redpill')
[/code]

[code lang="python"]
channel.queue_bind(exchange='test-exchange', queue='test-queue2', routing_key='bluepill')
[/code]



## Testing





##### Sending



[code lang="python"]
import pika
pika_cred = pika.PlainCredentials('guest', 'guest')
pika_conn_params = pika.ConnectionParameters('localhost', credentials=pika_cred)

pika_connection = pika.BlockingConnection(pika_conn_params)
channel = pika_connection.channel()
[/code]

Lets send a hello world message to queue1.

[code lang="python"]
channel.basic_publish(exchange='test-exchange', routing_key='redpill', body='Hello World!')
print(&quot; [x] Sent 'Hello World!'&quot;)
[/code]

Let's also send a hello world message to queue2.

[code lang="python"]
channel.basic_publish(exchange='test-exchange', routing_key='bluepill', body='Hello World2!')
print(&quot; [x] Sent 'Hello World!'&quot;)
[/code]

Let's send a hello world message to exchange with a routing_key, we have not defined, to see what happens

[code lang="python"]
channel.basic_publish(exchange='test-exchange', routing_key='greypill', body='Hello World3!')
print(&quot; [x] Sent 'Hello World!'&quot;)
[/code]

[x] Sent 'Hello World!'

[code lang="python"]
pika_connection.close()
[/code]



##### Reading



Reading for `test-queue1`

[code lang="python"]
pika_connection = pika.BlockingConnection(pika_conn_params)
channel = pika_connection.channel()
[/code]

[code lang="python"]
for each in channel.consume(queue='test-queue1', no_ack=True, inactivity_timeout=0):
if each:
print(each)
else:
break
[/code]

Reading from `test-queue2`

[code lang="python"]
pika_connection = pika.BlockingConnection(pika_conn_params)
channel = pika_connection.channel()
[/code]

[code lang="python"]
for each in channel.consume(queue='test-queue2', no_ack=True, inactivity_timeout=2):
if each:
print(each)
else:
break
[/code]
