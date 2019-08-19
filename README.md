# kafka_vs_rabbitmq
Kafka -

Design -
	• Partition centric design
	• To a topic, messages published are distributed into partition
	• In partition, messages are represented as a log stream
	• The consumer is responsible for moving through this stream
	• Messages from each partition are processed in-order only

SOURCE: https://content.pivotal.io/blog/understanding-when-to-use-rabbitmq-or-apache-kafka

![Kafka Design](https://content.cdntwrk.com/files/aHViPTYzOTc1JmNtZD1pdGVtZWRpdG9yaW1hZ2UmZmlsZW5hbWU9aXRlbWVkaXRvcmltYWdlXzVkMGMxMTc4ODNkYjgucG5nJnZlcnNpb249MDAwMCZzaWc9YTU1OGJlMWY4YzQwNGI4Zjg0MWJjOGM4Y2M3ZDRjODE%253D)

Major benefit
	• Kafka scales up to 100,000 messages/sec on a single server
Major limitation
	• Each partition can have only one logical consumer in the consumer group. i.e., when working with slow messages single issue, blocks all other messages submitted to this partition after that message.
Workaround 
	• Strategically implement - run another Kafka Consumer group and synchronize it with existing consumer in order to avoid duplicate message processing

Kafka can be used for high-ingress data streams and replay. It is an optimized message bus.
Kafka is useful in event driven architecture.

Background-
It is developed in Scala. It started out at LinkedIn as a way to connect different internal systems. Afterwards, Apache Software Foundation adopted Kafka within the ecosystem of products.



Primary Use-
Build applications that process and re-process streamed data on disk


License- Open source under Apache License 2.0

Developed -
Kafka is written in Scala (JVM).

Client Libraries-
To name a few - Ruby, Python, Java, Node.js
*Community driven open source clients available and adapter SDK's to build own system integrations. Configuration is performed using .properties file.

High Availability-
It supports high availability. Supports Horizonal Scaling.

Federated Queues-
Kafka doesn't support federated queues.

Kafka is capable of performing complex routing.

RabbitMQ -

Design -
	• Messages published to queues (through exchange points)
	• Multiple consumers can connect to a queue
	• Message broker distribute messages across all available consumers
	• Re-delivery of messages possible if the consumer fails
	• Delivery order guaranteed for queues with a single consumer


SOURCE: https://content.pivotal.io/blog/understanding-when-to-use-rabbitmq-or-apache-kafka



Major benefit
	• Huge number of development platforms supported with ease of use and maturity.
	• Additional benefit of working with slow consumers - if some consumer is stuck with some  slow processing other messages will stick to the queue as well unless other consumers are not added. In other words adding more consumers to the queue will bypass processing limitations. Just starting another RabbitMQ process will take care of everything.
Major limitation
	• RabbitMQ scales up to 20000 messages/sec on a single server
	
RabbitMQ is a mature, general purpose message broker with supports various standardized protocols like AMQP.
RabbitMQ facilitates cross language flexibility with AMQP.

Background-
It was developed to implement AMQP, an open wire protocol for messaging with powerful routing features. Java already has messaging standards like JMS, hence for non-java applications it is not helpful since that need distributed messaging which is severely limiting to any integration scenario, either microservice or monolithic.
Primary Use-
It process high throughput and reliable background jobs, communication and integration within and between applications

License- Open source under Mozilla Public License

Developed -
RabbitMQ is written in Erlang.

Client Libraries-
To name a few - .net, Ruby, Python, Java, Objective-C etc.
*Its client libraries are mature and well documented and are officially supported, backed by community plugins and support.

High Availability-
It does support high availability. It supports Vertical Scaling.

SOURCE-
https://stackoverflow.com/questions/42151544/is-there-any-reason-to-use-rabbitmq-over-kafka
https://www.cloudamqp.com/blog/2017-12-29-part1-rabbitmq-best-practice.html

NOTE: 
Horizontal scaling (scale by adding more machines) does not give you a better performance in RabbitMQ. Best performance is received when you do vertical scaling (scale by adding more power). I know this because I have been working with thousands of RabbitMQ clusters for many years now. You can do horizontal scaling in Rabbit, but that means that you also set up clustering between your nodes, which will slow down your setup. I wrote a guide about best practice for high performance vs high availability in RabbitMQ:

From <https://stackoverflow.com/questions/42151544/is-there-any-reason-to-use-rabbitmq-over-kafka> 


Federated Queues-
RabbitMQ has support for federated queues. This feature provides a way of balancing the load of single queue across nodes or clusters.A federated queue links to other queues called upstream queues. It will retrieve messages from upstream queues in order to satisfy demand for messages from local consumers. The upstream queues do not need to be reconfigured and they do not have to be on the same broker or same cluster.

It is a major advantage of RabbitMQ in an AutoScaling environment in multi-node environment like AKS (Azure Kubernetes Services). 


RabbitMQ isn't capable of complex routing scenarios.

