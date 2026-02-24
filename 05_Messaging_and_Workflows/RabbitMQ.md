# RabbitMQ

Your summary of the Publish-Subscribe (Pub/Sub) pattern and the comparison of different Pub/Sub messaging brokers like RabbitMQ, Kafka, and ActiveMQ is quite informative. Here's a bit more detail on each of these options to help users make an informed choice:

1. **RabbitMQ:**
   - **Language:** Built on Erlang.
   - **Protocols:** Supports various protocols, including AMQP, MQTT, and STOMP.
   - **Ease of Use:** Known for being developer-friendly.
   - **Use Cases:** Excellent for complex routing to multiple consumers.
   - **Scalability:** Suitable for a wide range of applications.

2. **Kafka:**
   - **Language:** Built on Scala and Java.
   - **Protocols:** Uses its proprietary Kafka Protocol over TCP.
   - **Scalability:** Highly scalable and can handle massive data volumes.
   - **Use Cases:** Ideal for real-time analytics, monitoring, data lakes, and aggregating data from different sources.
   - **Event Streaming:** Kafka is often used as an event streaming platform.

3. **ActiveMQ:**
   - **Language:** Built on Java.
   - **Protocols:** Supports various protocols like AMQP, STOMP, MQTT, and more.
   - **Features:** Provides a wide range of features and can be configured in various ways.
   - **Use Cases:** Commonly used in enterprise systems and excels in scenarios that require complex routing and message transformations.

In addition to these, here are a few other factors to consider when choosing a Pub/Sub messaging broker:

- **Community and Support:** Check the community size and availability of support or documentation for the chosen messaging broker.
  
- **Integration:** Consider how well the messaging broker integrates with your existing tech stack and tools.
  
- **Performance:** Evaluate the performance characteristics, such as latency and throughput, based on your requirements.
  
- **Scaling:** Ensure that the messaging broker can scale horizontally as your system grows.
  
- **Reliability:** Assess the broker's reliability features, like message durability and failover mechanisms.
  
- **Cost:** Factor in the cost of licensing, hardware, and maintenance when making your decision.

Ultimately, the choice of a Pub/Sub messaging broker should align with your specific use case, scalability needs, and the level of complexity you anticipate in your messaging patterns. Each of the options you mentioned has its strengths, so it's essential to carefully evaluate your requirements and choose the one that best fits your project's needs.

## Summary 
The Publish-Subscribe pattern, commonly known as Pub/Sub, is a messaging communication pattern used in distributed systems.

Here, the 'Publisher' sends messages without having to specify who the 'Subscriber' is.

Subscribers express interest in one or more topics and only receive messages that are of interest, without needing to know who the Publisher is.

This level of abstraction and decoupling is why Pub/Sub is such a big deal!

🌟 𝗪𝗵𝘆 𝗜𝘀 𝗣𝘂𝗯/𝗦𝘂𝗯 𝗦𝗼 𝗙𝗮𝗺𝗼𝘂𝘀?

• 𝗦𝗰𝗮𝗹𝗮𝗯𝗶𝗹𝗶𝘁𝘆: Easily add more publishers and subscribers to the system.
• 𝗗𝗲𝗰𝗼𝘂𝗽𝗹𝗶𝗻𝗴: Publishers and subscribers don't need to know each other, making the system modular and easy to extend.
• 𝗥𝗲𝗮𝗹-𝘁𝗶𝗺𝗲 𝗨𝗽𝗱𝗮𝘁𝗲𝘀: Enables real-time analytics and notifications.
• 𝗟𝗼𝗮𝗱 𝗕𝗮𝗹𝗮𝗻𝗰𝗶𝗻𝗴: Automatically balances the load among multiple subscribers.

🛠 𝗗𝗶𝗳𝗳𝗲𝗿𝗲𝗻𝘁 𝗣𝘂𝗯/𝗦𝘂𝗯 𝗧𝗼𝗼𝗹𝘀
There's no shortage of tools available for implementing Pub/Sub, including but not limited to:
• Google Cloud Pub/Sub
• AWS SNS & SQS
• Redis Pub/Sub
• MQTT
• ZeroMQ
• NATS
• Kafka
• RabbitMQ


🔍 𝗭𝗼𝗼𝗺𝗶𝗻𝗴 𝗶𝗻𝘁𝗼 𝗥𝗮𝗯𝗯𝗶𝘁𝗠𝗤, 𝗞𝗮𝗳𝗸𝗮, 𝗮𝗻𝗱 𝗔𝗰𝘁𝗶𝘃𝗲𝗠𝗤
Let's briefly look at how each of these stand out:

1️⃣ 𝗥𝗮𝗯𝗯𝗶𝘁𝗠𝗤
• 𝗟𝗮𝗻𝗴𝘂𝗮𝗴𝗲: Built on Erlang
• 𝗣𝗿𝗼𝘁𝗼𝗰𝗼𝗹𝘀: Supports a multitude of protocols, including AMQP, MQTT, and STOMP.
• 𝗘𝗮𝘀𝗲 𝗼𝗳 𝗨𝘀𝗲: Known for being developer-friendly.
• 𝗨𝘀𝗲-𝗰𝗮𝘀𝗲: Excellent for complex routing to multiple consumers.

2️⃣ 𝗞𝗮𝗳𝗸𝗮
• 𝗟𝗮𝗻𝗴𝘂𝗮𝗴𝗲: Built on Scala and Java
• 𝗣𝗿𝗼𝘁𝗼𝗰𝗼𝗹𝘀: Proprietary Kafka Protocol over TCP
• 𝗦𝗰𝗮𝗹𝗮𝗯𝗶𝗹𝗶𝘁𝘆: Highly scalable with the ability to handle huge volumes of data.
• 𝗨𝘀𝗲-𝗰𝗮𝘀𝗲: Perfect for real-time analytics and monitoring, data lakes, aggregating data from different sources.

3️⃣ 𝗔𝗰𝘁𝗶𝘃𝗲𝗠𝗤
• 𝗟𝗮𝗻𝗴𝘂𝗮𝗴𝗲: Built on Java
• 𝗣𝗿𝗼𝘁𝗼𝗰𝗼𝗹𝘀: Supports various protocols like AMQP, STOMP, MQTT, and more.
• 𝗙𝗹𝗲𝘅𝗶𝗯𝗶𝗹𝗶𝘁𝘆: Provides a lot of features and can be used in multiple configurations.
• 𝗨𝘀𝗲-𝗰𝗮𝘀𝗲: Often used in enterprise systems and excels in scenarios that require complex routing and transformations.

🤔 𝗦𝗼, 𝘄𝗵𝗶𝗰𝗵 𝗼𝗻𝗲 𝘀𝗵𝗼𝘂𝗹𝗱 𝘆𝗼𝘂 𝗰𝗵𝗼𝗼𝘀𝗲?

- If you need advanced routing and a variety of protocol supports, 𝗥𝗮𝗯𝗯𝗶𝘁𝗠𝗤 could be the one.
- If you're dealing with massive streams of data and require a robust solution, go for 𝗞𝗮𝗳𝗸𝗮.
- If you're in an enterprise setting looking for a jack-of-all-trades, 𝗔𝗰𝘁𝗶𝘃𝗲𝗠𝗤 could be a good fit.

Choosing the right Pub/Sub messaging broker depends on your specific requirements, so assess carefully! 🎯

## Videos

 * [Intro To RabbitMQ](https://www.youtube.com/watch?v=bfVddTJNiAw)
	> [<img src="https://img.youtube.com/vi/bfVddTJNiAw/0.jpg" width="200">](https://www.youtube.com/watch?v=bfVddTJNiAw "Intro To RabbitMQ by IAmTimCorey 79,921 views 54 minutes")
 * [What is RabbitMQ?](https://www.youtube.com/watch?v=7rkeORD4jSw)
	> [<img src="https://img.youtube.com/vi/7rkeORD4jSw/0.jpg" width="200">](https://www.youtube.com/watch?v=7rkeORD4jSw "What is RabbitMQ? by IBM Technology 294,353 views 10 minutes, 10 seconds")
 * [20h - Case Full Cycle: Desafios da construção de um microsserviço  |  21h - RabbitMQ na Prática](https://www.youtube.com/watch?v=3aTb8a_F4dQ)
	> [<img src="https://img.youtube.com/vi/3aTb8a_F4dQ/0.jpg" width="200">](https://www.youtube.com/watch?v=3aTb8a_F4dQ "20h - Case Full Cycle: Desafios da construção de um microsserviço  |  21h - RabbitMQ na Prática by Full Cycle 5,851 views 3 hours, 15 minutes")
