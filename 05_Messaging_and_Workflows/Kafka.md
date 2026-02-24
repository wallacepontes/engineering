# Kafka

## Why is Kafka fast? What is the secret?

Kafka is fast because it uses a publish-subscribe model and a log-based storage system. This allows it to handle high throughput and low-latency data streams. Additionally, it uses a partitioning system to distribute data across multiple servers, which allows it to scale horizontally. The secret to Kafka's performance is its ability to handle high volume and high velocity data streams with a high level of fault-tolerance and low latency.

## What does it even mean that Kafka is fast? Are we talking latency? Are we talking throughput?

When we say that Kafka is "fast", it can refer to both latency and throughput.

Latency refers to the amount of time it takes for a piece of data to be processed and made available to downstream systems. Kafka is designed to have low latency, meaning that messages can be processed and made available to consumers very quickly.

Throughput refers to the number of messages that can be processed per second. Kafka is designed to handle high throughput, meaning it can process large amounts of data in a short period of time. This is achieved by its ability to handle large numbers of concurrent connections and its ability to distribute data across multiple servers.

Kafka's publish-subscribe model and log-based storage system also allow it to handle high levels of fault-tolerance and data durability, which is crucial in many big data use-cases. 

All these features make Kafka a popular choice for real-time data streaming and data integration scenarios.

## It is fast compared to what?

Kafka is often compared to other messaging systems and data streaming platforms, such as RabbitMQ, ActiveMQ, and Storm. These systems are also capable of handling high throughput and low-latency data streams, but they may not have the same level of scalability and fault-tolerance that Kafka provides.

Compared to traditional message queues, Kafka is considered to be faster in terms of the number of messages that can be processed per second, and it can handle a greater number of concurrent connections. It is also able to handle large amounts of data and maintain low latency, which is useful for real-time data streaming and data integration scenarios.

Kafka is also considered to be faster than batch-oriented data integration solutions like ETL (Extract, Transform, Load) pipelines, since it can handle real-time data streams rather than batches of data that are processed at regular intervals.

It is worth to note that it really depends on the use case and the specific requirements of the system. The choice of technology for a particular use-case will vary depending on the specific needs of the organization.


## What are some of the design decisions that help Kafka move a lot of data quickly?

There are several design decisions that have helped Kafka move a lot of data quickly:

1. Log-based storage: Kafka stores all data in a log-based storage system, which allows it to write data quickly and efficiently. It also allows for fast recovery and replication of data.

2. Partitioning: Kafka distributes data across multiple servers by partitioning it. This allows it to scale horizontally and handle large amounts of data. Each partition can be processed by a separate thread, which helps to increase the overall throughput.

3. Producers and Consumers: Kafka uses a publish-subscribe model, where producers write data to topics and consumers read from those topics. This allows for a high degree of parallelism and allows for efficient data processing.

4. Compression: Kafka uses a variety of compression algorithms to compress the data before sending it over the network. This reduces the amount of data that needs to be transferred, which can help to increase overall throughput.

5. In-memory data structures: Kafka uses in-memory data structures such as log segments and indexes to keep track of data. This allows it to quickly locate and read data, which can help to reduce latency.

6. Network Protocol: Kafka uses a binary protocol to transfer data over the network, which is more efficient than text-based protocols.

7. Batch Processing: Kafka allows for batch processing of messages, that means consumer can read multiple messages at once, which can help to increase throughput.

All these design decisions help Kafka to handle high-throughput, low-latency data streams, and provide a high level of scalability and fault-tolerance.

## How about Kafka's reliance on sequential I/O.

Kafka's reliance on sequential I/O is one of the design decisions that contribute to its high performance.

Sequential I/O refers to the process of reading and writing data in a sequential manner, rather than randomly accessing different parts of a file or disk. By using sequential I/O, Kafka can write data to disk more quickly and efficiently. This is because modern hard drives are optimized for sequential access and can read and write data much faster when it is laid out in a contiguous manner.

Additionally, Kafka uses a log-based storage system, which means that data is written to disk in the order in which it is received. This allows for more efficient use of disk space and faster recovery of data in the event of a failure.

Kafka also uses a combination of memory and disk storage to keep track of data. It uses in-memory data structures such as log segments and indexes to quickly locate and read data. When a log segment is full, it is written to disk and the oldest segment can be deleted. This helps to balance the need for fast access to data with the need to manage disk space.

Overall, Kafka's reliance on sequential I/O allows it to handle high-throughput and low-latency data streams while also providing a high level of fault-tolerance and data durability.

## And how about the zero copy principle

The zero copy principle is another design decision that helps Kafka to move data quickly.

The zero copy principle refers to the idea of avoiding unnecessary data copying when transferring data between different parts of a system. In traditional systems, data may be copied multiple times as it is passed from one component to another. But with zero copy, data is transferred directly from one component to another without the need for an intermediate copy.

Kafka makes use of zero copy principle by allowing data to be transferred directly from the producer's buffer to the consumer's buffer, without the need for an intermediate copy. This is achieved by using memory-mapped files and transfer of ownership semantics, which allows data to be passed from one component to another without the need for an additional copy.

The use of zero copy principle can help to reduce the amount of memory and CPU resources required to transfer data, which can help to increase overall throughput and reduce latency.

It's worth to mention that Zero-copy is not only applied to Kafka but also other messaging systems and data streaming platforms. It's a general principle that is used to improve the performance of data transfer.

## Videos

 * [Apache Kafka Explained (Comprehensive Overview)](https://www.youtube.com/watch?v=JalUUBKdcA0)
	> [<img src="https://img.youtube.com/vi/JalUUBKdcA0/0.jpg" width="200">](https://www.youtube.com/watch?v=JalUUBKdcA0 "Apache Kafka Explained (Comprehensive Overview) by Finematics 205,548 views 19 minutes")
 * [1. Introduction | Apache Kafka Fundamentals](https://www.youtube.com/watch?v=-DyWhcX3Dpc)
	> [<img src="https://img.youtube.com/vi/-DyWhcX3Dpc/0.jpg" width="200">](https://www.youtube.com/watch?v=-DyWhcX3Dpc "1. Introduction | Apache Kafka Fundamentals by Confluent 114,686 views 1 minute, 1 second")
 * [Apache Kafka 101 for Beginners Course Trailer (2023)](https://www.youtube.com/watch?v=j4bqyAMMb7o)
	> [<img src="https://img.youtube.com/vi/j4bqyAMMb7o/0.jpg" width="200">](https://www.youtube.com/watch?v=j4bqyAMMb7o "Apache Kafka 101 for Beginners Course Trailer (2023) by Confluent 108,938 views 1 minute, 18 seconds")
 * [4. How Kafka Works | Apache Kafka Fundamentals](https://www.youtube.com/watch?v=jY02MB-sz8I)
	> [<img src="https://img.youtube.com/vi/jY02MB-sz8I/0.jpg" width="200">](https://www.youtube.com/watch?v=jY02MB-sz8I "4. How Kafka Works | Apache Kafka Fundamentals by Confluent 176,953 views 26 minutes")
 * [Apache Kafka in 6 minutes](https://www.youtube.com/watch?v=Ch5VhJzaoaI)
	> [<img src="https://img.youtube.com/vi/Ch5VhJzaoaI/0.jpg" width="200">](https://www.youtube.com/watch?v=Ch5VhJzaoaI "Apache Kafka in 6 minutes by James Cutajar 892,548 views 6 minutes, 48 seconds")
 * [Apache Kafka Crash Course | What is Kafka?](https://www.youtube.com/watch?v=ZJJHm_bd9Zo)
	> [<img src="https://img.youtube.com/vi/ZJJHm_bd9Zo/0.jpg" width="200">](https://www.youtube.com/watch?v=ZJJHm_bd9Zo "Apache Kafka Crash Course | What is Kafka? by Piyush Garg 286,914 views 1 hour, 17 minutes")
 * [Building and Designing Events and Event Streams with Apache Kafka](https://www.youtube.com/watch?v=zOWJ5hAcp9Y)
	> [<img src="https://img.youtube.com/vi/zOWJ5hAcp9Y/0.jpg" width="200">](https://www.youtube.com/watch?v=zOWJ5hAcp9Y "Building and Designing Events and Event Streams with Apache Kafka by Confluent 1,787 views 53 minutes")
 * [Amazon S3 Kafka Connector Setup &amp; Configuration](https://www.youtube.com/watch?v=joAdluM4Xfo)
	> [<img src="https://img.youtube.com/vi/joAdluM4Xfo/0.jpg" width="200">](https://www.youtube.com/watch?v=joAdluM4Xfo "Amazon S3 Kafka Connector Setup &amp; Configuration by Confluent 3,908 views 7 minutes, 13 seconds")
 * [What is Kafka?](https://www.youtube.com/watch?v=aj9CDZm0Glc)
	> [<img src="https://img.youtube.com/vi/aj9CDZm0Glc/0.jpg" width="200">](https://www.youtube.com/watch?v=aj9CDZm0Glc "What is Kafka? by IBM Technology 422,634 views 9 minutes, 17 seconds")
 * [You want to use Kafka? Or do you really need a Queue?](https://www.youtube.com/watch?v=dpl4xKkPxHY)
	> [<img src="https://img.youtube.com/vi/dpl4xKkPxHY/0.jpg" width="200">](https://www.youtube.com/watch?v=dpl4xKkPxHY "You want to use Kafka? Or do you really need a Queue? by CodeOpinion 22,081 views 11 minutes, 43 seconds")
 * [Apache Kafka Crash Course](https://www.youtube.com/watch?v=R873BlNVUB4)
	> [<img src="https://img.youtube.com/vi/R873BlNVUB4/0.jpg" width="200">](https://www.youtube.com/watch?v=R873BlNVUB4 "Apache Kafka Crash Course by Hussein Nasser 401,162 views 1 hour, 18 minutes")
 * [Kafka (Plataforma de Mensageria e Streaming) // Dicionário do Programador](https://www.youtube.com/watch?v=qOqXz5Qv_-8)
	> [<img src="https://img.youtube.com/vi/qOqXz5Qv_-8/0.jpg" width="200">](https://www.youtube.com/watch?v=qOqXz5Qv_-8 "Kafka (Plataforma de Mensageria e Streaming) // Dicionário do Programador by Código Fonte TV 61,623 views 11 minutes, 3 seconds")
 * [Event-Driven Architectures Done Right, Apache Kafka • Tim Berglund • Devoxx Poland 2021](https://www.youtube.com/watch?v=A_mstzRGfIE)
	> [<img src="https://img.youtube.com/vi/A_mstzRGfIE/0.jpg" width="200">](https://www.youtube.com/watch?v=A_mstzRGfIE "Event-Driven Architectures Done Right, Apache Kafka • Tim Berglund • Devoxx Poland 2021 by Devoxx Poland 174,151 views 50 minutes")
 * [Intelligent Kafka message routing with Drools DMN Engine &amp; Camel](https://www.youtube.com/watch?v=tNe6QU1Yq8U)
	> [<img src="https://img.youtube.com/vi/tNe6QU1Yq8U/0.jpg" width="200">](https://www.youtube.com/watch?v=tNe6QU1Yq8U "Intelligent Kafka message routing with Drools DMN Engine &amp; Camel by Matteo Mortari 3,037 views 12 minutes, 16 seconds")
 * [System Design: Why is Kafka fast?](https://www.youtube.com/watch?v=UNUz1-msbOM)
	> [<img src="https://img.youtube.com/vi/UNUz1-msbOM/0.jpg" width="200">](https://www.youtube.com/watch?v=UNUz1-msbOM "System Design: Why is Kafka fast? by ByteByteGo 1,026,220 views 5 minutes, 2 seconds")
 * [RABBITMQ VS KAFKA - QUAL É MELHOR PARA SUA APLICAÇÃO?](https://www.youtube.com/watch?v=xW34VRLErmU)
	> [<img src="https://img.youtube.com/vi/xW34VRLErmU/0.jpg" width="200">](https://www.youtube.com/watch?v=xW34VRLErmU "RABBITMQ VS KAFKA - QUAL É MELHOR PARA SUA APLICAÇÃO? by Lucas Gertel 4,878 views 6 minutes, 37 seconds")
 * [Cloud-Native 5G, MEC and OSS/BSS/OTT Telco with Apache Kafka and Kubernetes](https://www.youtube.com/watch?v=yoRUC0sFbJo)
	> [<img src="https://img.youtube.com/vi/yoRUC0sFbJo/0.jpg" width="200">](https://www.youtube.com/watch?v=yoRUC0sFbJo "Cloud-Native 5G, MEC and OSS/BSS/OTT Telco with Apache Kafka and Kubernetes by Kai Wähner 5,820 views 29 minutes")
* [Kafka do Zero: Mão na massa](https://www.youtube.com/watch?v=PppMhofKzy4)
	> [<img src="https://img.youtube.com/vi/PppMhofKzy4/0.jpg" width="200">](https://www.youtube.com/watch?v=PppMhofKzy4 "Kafka do Zero: Mão na massa by Full Cycle 61,000 views 34 minutes, 24 seconds")

## References

1. https://kafka.apache.org/
2. https://stackoverflow.com/questions/43045590/kafka-setup-with-docker-compose
3. https://medium.com/experiencecode/kafka-produzindo-mensagens-com-java-13d326223507
4. https://ivanqueiroz.dev/2020/09/2020-09-26-consumer-producer-kafka.html
5. https://medium.com/wix-engineering/troubleshooting-kafka-for-2000-microservices-at-wix-986ee382fd1e
6. 

