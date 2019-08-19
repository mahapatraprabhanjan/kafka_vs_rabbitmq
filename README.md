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


