# Amazon Simple Queue Service (SQS)

## Table of Contents

- [Amazon Simple Queue Service (SQS)](#amazon-simple-queue-service-sqs)
  - [Table of Contents](#table-of-contents)
  - [🧭 1. What is Amazon SQS?](#-1-what-is-amazon-sqs)
    - [🔑 Key Benefits:](#-key-benefits)
  - [⚙️ 2. Prerequisites](#️-2-prerequisites)
  - [🏁 3. Create a Queue via AWS Console](#-3-create-a-queue-via-aws-console)
  - [✉️ 4. Send a Message (from Console)](#️-4-send-a-message-from-console)
  - [📥 5. Receive \& Delete Messages (from Console)](#-5-receive--delete-messages-from-console)
  - [⚡ 6. Using the AWS CLI](#-6-using-the-aws-cli)
    - [a) Create a queue](#a-create-a-queue)
    - [b) Get the queue URL](#b-get-the-queue-url)
    - [c) Send a message](#c-send-a-message)
    - [d) Receive a message](#d-receive-a-message)
    - [e) Delete the message](#e-delete-the-message)
  - [💻 7. Using SQS Programmatically (Node.js Example)](#-7-using-sqs-programmatically-nodejs-example)
  - [🧩 8. FIFO Queue Example (Optional)](#-8-fifo-queue-example-optional)
  - [🔔 9. Best Practices](#-9-best-practices)
  - [🧠 10. When to Use SQS](#-10-when-to-use-sqs)
  - [📘 Summary](#-summary)
  - [References](#references)

Perfect 👍 — here’s a **complete “Getting Started with Amazon Simple Queue Service (Amazon SQS)” tutorial**, designed to take you from zero to sending and receiving your first messages — both from the **AWS Console** and **programmatically**.

---

## 🧭 1. What is Amazon SQS?

**Amazon Simple Queue Service (SQS)** is a **fully managed message queuing service** that enables **asynchronous communication** between microservices, distributed systems, and serverless applications.

### 🔑 Key Benefits:

* Decouples components — improves scalability and fault tolerance.
* Automatically scales to handle any load.
* Guarantees **at-least-once delivery**.
* Offers **two queue types**:

  * **Standard Queue** – Unlimited throughput, best-effort ordering, and at-least-once delivery.
  * **FIFO Queue** – First-In-First-Out ordering with exactly-once processing.

---

## ⚙️ 2. Prerequisites

Before starting:

* You need an **AWS Account**.
* Basic knowledge of AWS IAM (permissions) is helpful.
* (Optional) **AWS CLI** or **SDK** installed if you’ll use code.

---

## 🏁 3. Create a Queue via AWS Console

1. Open **Amazon SQS Console** → [https://console.aws.amazon.com/sqs](https://console.aws.amazon.com/sqs)
2. Click **“Create queue”**.
3. Choose the **Queue type**:

   * `Standard` (recommended for most cases)
   * `FIFO` (if message order matters)
4. Configure basic settings:

   * Queue name (e.g., `MyTestQueue`)
   * Leave defaults for now (we’ll tune them later)
5. Click **“Create queue”**.

✅ You’ve just created your first queue!

---

## ✉️ 4. Send a Message (from Console)

1. Open your queue (`MyTestQueue`).
2. Click **“Send and receive messages”**.
3. In the “Message body” field, type:

   ```
   Hello from Cloud!
   ```
4. Click **Send message**.
5. You should see it appear in the **Messages available** counter.

---

## 📥 5. Receive & Delete Messages (from Console)

1. Click **Poll for messages**.
2. You’ll see your message appear.
3. Expand it to view details (Message ID, Body, Attributes, etc.).
4. Click **Delete** to remove it from the queue (to prevent redelivery).

✅ You’ve now sent and consumed a message successfully.

---

## ⚡ 6. Using the AWS CLI

Let’s do the same steps via the AWS Command Line Interface.

### a) Create a queue

```bash
aws sqs create-queue --queue-name MyTestQueue
```

### b) Get the queue URL

```bash
aws sqs get-queue-url --queue-name MyTestQueue
```

You’ll get something like:

```
{
  "QueueUrl": "https://sqs.us-east-1.amazonaws.com/123456789012/MyTestQueue"
}
```

### c) Send a message

```bash
aws sqs send-message \
  --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/MyTestQueue \
  --message-body "Hello from AWS CLI"
```

### d) Receive a message

```bash
aws sqs receive-message \
  --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/MyTestQueue
```

### e) Delete the message

Use the `ReceiptHandle` returned by the previous command:

```bash
aws sqs delete-message \
  --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/MyTestQueue \
  --receipt-handle <YOUR_RECEIPT_HANDLE>
```

---

## 💻 7. Using SQS Programmatically (Node.js Example)

Install AWS SDK:

```bash
npm install aws-sdk
```

Create a file `sqs-example.js`:

```js
import AWS from "aws-sdk";

AWS.config.update({ region: "us-east-1" });

const sqs = new AWS.SQS();
const queueUrl = "https://sqs.us-east-1.amazonaws.com/123456789012/MyTestQueue";

// Send message
async function sendMessage() {
  const params = {
    MessageBody: "Hello from Node.js!",
    QueueUrl: queueUrl,
  };
  const result = await sqs.sendMessage(params).promise();
  console.log("Message sent:", result.MessageId);
}

// Receive message
async function receiveMessage() {
  const params = {
    QueueUrl: queueUrl,
    MaxNumberOfMessages: 1,
    WaitTimeSeconds: 5,
  };
  const result = await sqs.receiveMessage(params).promise();
  if (result.Messages) {
    console.log("Message received:", result.Messages[0].Body);

    // Delete message
    await sqs.deleteMessage({
      QueueUrl: queueUrl,
      ReceiptHandle: result.Messages[0].ReceiptHandle,
    }).promise();
    console.log("Message deleted");
  } else {
    console.log("No messages found");
  }
}

await sendMessage();
await receiveMessage();
```

Run:

```bash
node sqs-example.js
```

✅ You’ll see the send/receive cycle completed programmatically.

---

## 🧩 8. FIFO Queue Example (Optional)

If you want guaranteed order and exactly-once processing:

1. Create a queue named **MyQueue.fifo**.
2. When sending messages, **include a MessageGroupId**:

   ```bash
   aws sqs send-message \
     --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/MyQueue.fifo \
     --message-body "Message #1" \
     --message-group-id "GroupA"
   ```

This ensures messages with the same `MessageGroupId` are processed **in order**.

---

## 🔔 9. Best Practices

✅ **Use Dead Letter Queues (DLQ)** – to capture failed messages.
✅ **Enable Server-Side Encryption (SSE)** – for sensitive data.
✅ **Short/Long Polling** – prefer *long polling* (`WaitTimeSeconds > 0`) to reduce empty responses.
✅ **Batch Operations** – send/receive up to 10 messages per API call to improve efficiency.
✅ **Visibility Timeout** – adjust properly to ensure consumers have time to process messages.
✅ **Use FIFO queues sparingly** – only when ordering and exactly-once semantics are critical.

---

## 🧠 10. When to Use SQS

| Use Case                   | Why SQS Works Well                               |
| -------------------------- | ------------------------------------------------ |
| Decoupling microservices   | Prevents direct dependency between components    |
| Event-driven architectures | Acts as a buffer between producers and consumers |
| Load leveling              | Smooths out traffic spikes                       |
| Retry & resilience         | Automatically retries and isolates failures      |
| Asynchronous tasks         | Background jobs or delayed processing            |

---

## 📘 Summary

| Concept                | Description                                     |
| ---------------------- | ----------------------------------------------- |
| **Queue**              | Message container (Standard or FIFO)            |
| **Message**            | Data payload sent between systems               |
| **Producer**           | Sends messages to the queue                     |
| **Consumer**           | Retrieves and processes messages                |
| **Visibility Timeout** | Time during which message is hidden from others |
| **Dead Letter Queue**  | Stores messages that fail to be processed       |

---

Would you like me to extend this with a **hands-on lab** showing how to connect **SQS with AWS Lambda or an API Gateway**, so messages are processed automatically?

## References

1. https://aws.amazon.com/pt/sqs/
2. 