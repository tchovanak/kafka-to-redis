	
## zookeeper  
* open-source server which enables highly reliable distributed coordination https://www.cloudkarafka.com/blog/2018-07-04-cloudkarafka_what_is_zookeeper.html
* acts as a centralized service and is used to maintain naming and configuration data and to provide flexible and robust synchronization within distributed systems. 
  Zookeeper keeps track of status of the Kafka cluster nodes and it also keeps track of Kafka topics, partitions etc.
  The Zookeeper atomic broadcast (ZAB) protocol i s the brains of the whole system, making it possible for Zookeeper to act as an atomic broadcast system and issue orderly updates.
  atomic broadcast or total order broadcast is a broadcast where all correct processes in a system of multiple processes receive the same set of messages in the same order; that is, the same sequence of messages.[1][2] The broadcast is termed "atomic" because it either eventually completes correctly at all participants, or all participants abort without side effects.
	
* Why is zookeeper necessary for Apache Kafka ? 
	Controller/Leader election - whenever a node shuts down, a new controller/leader can be elected and it can also be made sure that at any given time, there is only one controller and all the follower nodes have agreed on that.
	Configuration Of Topics
	Access control lists

# apache avro 
	https://www.confluent.io/blog/avro-kafka-data/
	open source data serialization system that helps with data exchange between systems, programming languages, and processing frameworks.
	helps define a binary format for your data, as well as map it to the programming language of your choice.
	It comes with a very sophisticated schema description language that describes data.
	It has a direct mapping to and from JSON
	
# schema registry 
	serving layer for your metadata. It provides a RESTful interface for storing and retrieving Avro schemas.
	Kafka Connect and Schema Registry integrate to capture schema information from connectors. 
	
# kafka connect
	framework for connecting Kafka with external systems such as databases, key-value stores, search indexes, and file systems.
	Source Connector
	Sink Connector - delivers data from Kafka topics into secondary indexes such as Elasticsearch or batch systems such as Hadoop for offline analysis.
		
* na nastartovanie kafka connect je nutne navysit ram pre docker (asi na 8GB)

* konfiguracia kafka-connect	
	CONNECT_PLUGIN_PATH - definuje cestu k pluginom (napr. aj k elasticsearch sink connectoru)
	
# redis
	Redis is “an open source, in-memory data structure store, used as a database, 
	cache and message broker”. 
