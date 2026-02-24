# Localstack Cloud

## Table of Contents

- [Localstack Cloud](#localstack-cloud)
  - [Table of Contents](#table-of-contents)
  - [🧭 What Is LocalStack?](#-what-is-localstack)
    - [Key differences between the free and paid versions](#key-differences-between-the-free-and-paid-versions)
  - [🧱 1. Installation](#-1-installation)
    - [**Option 1 – Using Docker (Recommended)**](#option-1--using-docker-recommended)
      - [Requirements:](#requirements)
      - [Steps:](#steps)
    - [**Option 2 – Using pip (Python)**](#option-2--using-pip-python)
    - [**Option 3 – Using npm**](#option-3--using-npm)
  - [⚙️ 2. Setting up AWS CLI to use LocalStack](#️-2-setting-up-aws-cli-to-use-localstack)
    - [Step 1: Install AWS CLI](#step-1-install-aws-cli)
    - [Step 2: Configure AWS CLI](#step-2-configure-aws-cli)
    - [Step 3: Use `--endpoint-url` to point to LocalStack](#step-3-use---endpoint-url-to-point-to-localstack)
  - [🚀 3. Basic Example – Node.js + LocalStack (S3)](#-3-basic-example--nodejs--localstack-s3)
    - [1️⃣ Install dependencies](#1️⃣-install-dependencies)
    - [2️⃣ Create a simple script `s3-local.js`](#2️⃣-create-a-simple-script-s3-localjs)
    - [3️⃣ Run it](#3️⃣-run-it)
  - [🧩 4. Supported AWS Services](#-4-supported-aws-services)
  - [🧪 5. Example with Docker Compose (more convenient)](#-5-example-with-docker-compose-more-convenient)
  - [🧰 6. Integration with Tests](#-6-integration-with-tests)
  - [🧩 7. Useful Tools](#-7-useful-tools)
  - [🧹 8. Cleanup \& Stop](#-8-cleanup--stop)
  - [🧠 Summary](#-summary)
  - [Video](#video)
  - [References](#references)

Perfect 👍 — let’s go step-by-step into **“Getting Started with LocalStack”**, a very useful tool for simulating AWS services **locally**.

---

## 🧭 What Is LocalStack?

**LocalStack** is a *local AWS cloud emulator*.
It allows you to run AWS services (like S3, Lambda, DynamoDB, SQS, etc.) on your machine — **without using real AWS accounts**.

It’s ideal for:

- Local development and testing of cloud-based applications.
- CI/CD pipelines that require AWS components.
- Avoiding AWS costs during early development.

LocalStack offers a tiered service model, where the core functionality is available for free, while advanced features and a wider range of emulated services are part of the paid Pro and Enterprise plans.

### Key differences between the free and paid versions

- Community Edition (Free): Includes basic emulation of services like S3, Lambda, SQS, and DynamoDB. It's a great starting point for individual developers and small projects.
- Pro/Enterprise Editions (Paid): Unlock more sophisticated features and a much broader selection of emulated services (including ECS, EKS, API Gateway, AppSync, Kinesis, and more), advanced debugging tools, and enterprise-grade support [1]. 

Many developers find the free tier sufficient for local development and testing of core AWS services, while larger teams or projects with complex architectural needs often benefit from the comprehensive feature set in the paid versions. 

For a detailed breakdown, you can review the official LocalStack Pricing page or visit the LocalStack Documentation to see the full list of supported services. 

---

## 🧱 1. Installation

You have 3 main installation options.

### **Option 1 – Using Docker (Recommended)**

LocalStack runs best in Docker containers.

#### Requirements:

* [Docker Desktop](https://www.docker.com/products/docker-desktop)
* [Docker Compose](https://docs.docker.com/compose/)

#### Steps:

```bash
# Pull the latest LocalStack image
docker pull localstack/localstack

# Run LocalStack container
docker run --rm -it -p 4566:4566 -p 4571:4571 localstack/localstack
```

💡 Default port `4566` is the main gateway for all AWS services.

---

### **Option 2 – Using pip (Python)**

If you want to install it as a Python package:

```bash
pip install localstack
localstack start
```

---

### **Option 3 – Using npm**

Useful if you’re developing in Node.js:

```bash
npm install -g localstack
localstack start
```

---

## ⚙️ 2. Setting up AWS CLI to use LocalStack

You’ll need the AWS CLI configured to point to LocalStack.

### Step 1: Install AWS CLI

```bash
pip install awscli
```

### Step 2: Configure AWS CLI

```bash
aws configure
```

Enter any dummy values (LocalStack doesn’t verify them):

```
AWS Access Key ID: test
AWS Secret Access Key: test
Default region name: us-east-1
Default output format: json
```

### Step 3: Use `--endpoint-url` to point to LocalStack

Example with S3:

```bash
aws --endpoint-url=http://localhost:4566 s3 mb s3://my-local-bucket
aws --endpoint-url=http://localhost:4566 s3 ls
```

---

## 🚀 3. Basic Example – Node.js + LocalStack (S3)

### 1️⃣ Install dependencies

```bash
npm init -y
npm install aws-sdk
```

### 2️⃣ Create a simple script `s3-local.js`

```js
const AWS = require('aws-sdk');

const s3 = new AWS.S3({
  endpoint: 'http://localhost:4566',
  s3ForcePathStyle: true,
  accessKeyId: 'test',
  secretAccessKey: 'test',
  region: 'us-east-1',
});

async function main() {
  await s3.createBucket({ Bucket: 'my-local-bucket' }).promise();
  console.log('Bucket created!');

  const data = await s3.listBuckets().promise();
  console.log('Buckets:', data.Buckets);
}

main().catch(console.error);
```

### 3️⃣ Run it

```bash
node s3-local.js
```

✅ You’ll see the created bucket listed from your LocalStack instance — no real AWS calls made!

---

## 🧩 4. Supported AWS Services

LocalStack supports many AWS services locally (especially in the **free tier**):

| Category       | Services                          |
| -------------- | --------------------------------- |
| **Storage**    | S3, DynamoDB                      |
| **Messaging**  | SQS, SNS                          |
| **Compute**    | Lambda                            |
| **API**        | API Gateway                       |
| **IAM**        | Users, Roles, Policies            |
| **Monitoring** | CloudWatch                        |
| **Networking** | CloudFormation, Route53 (partial) |

🟢 The **Pro** version adds even more: ECS, EKS, CloudFront, Step Functions, etc.

---

## 🧪 5. Example with Docker Compose (more convenient)

Create a `docker-compose.yml` file:

```yaml
version: "3.8"
services:
  localstack:
    image: localstack/localstack
    container_name: localstack
    ports:
      - "4566:4566"
    environment:
      - SERVICES=s3,sqs,lambda,dynamodb
      - DEBUG=1
      - DATA_DIR=/tmp/localstack/data
    volumes:
      - "./localstack-data:/tmp/localstack"
```

Start it:

```bash
docker compose up
```

---

## 🧰 6. Integration with Tests

In CI/CD or integration tests, you can:

* Start LocalStack before tests (via Docker or CLI).
* Run your app pointing to LocalStack URLs.
* Tear down after test completion.

Example with Jest:

```js
beforeAll(async () => {
  // spin up localstack with docker-compose before tests
});

afterAll(async () => {
  // stop docker-compose
});
```

---

## 🧩 7. Useful Tools

| Tool                       | Description                                               |
| -------------------------- | --------------------------------------------------------- |
| **LocalStack Web UI**      | `http://localhost:4566/_localstack` – visualize resources |
| **awslocal**               | A CLI wrapper for AWS CLI that auto-points to LocalStack  |
| **LocalStack Cloud Pods**  | Save/restore local environments across sessions           |
| **Terraform + LocalStack** | Test IaC templates locally                                |

Install `awslocal`:

```bash
pip install awscli-local
awslocal s3 ls
```

---

## 🧹 8. Cleanup & Stop

Stop LocalStack container:

```bash
docker stop localstack
```

Remove stored data:

```bash
rm -rf localstack-data
```

---

## 🧠 Summary

| Step | Description                             |
| ---- | --------------------------------------- |
| 1    | Install LocalStack (Docker recommended) |
| 2    | Configure AWS CLI to use it             |
| 3    | Run services locally on port 4566       |
| 4    | Test your app (S3, SQS, Lambda, etc.)   |
| 5    | Integrate in tests or CI pipelines      |

---

Would you like me to extend this tutorial to include **Lambda + API Gateway example using LocalStack**, so you can simulate a full serverless flow locally?

## Video

 * [Run AWS Locally with Docker (LocalStack)](https://www.youtube.com/watch?v=jz7oq-Viwew)
	> [<img src="https://img.youtube.com/vi/jz7oq-Viwew/0.jpg" width="200">](https://www.youtube.com/watch?v=jz7oq-Viwew "In this video, I’m going to show you LocalStack. It’s a tool that lets you run AWS services like S3, Lambda, DynamoDB, API Gateway, and SQS right on your own machine using Docker. by Better Stack 12,122 views 4 minutes")

## References 

1. http://localstack.cloud/