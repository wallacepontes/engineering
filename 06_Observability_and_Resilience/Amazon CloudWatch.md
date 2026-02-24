# Amazon CloudWatch

## Table of Contents

- [Amazon CloudWatch](#amazon-cloudwatch)
  - [Table of Contents](#table-of-contents)
  - [🧭 1. What Is Amazon CloudWatch?](#-1-what-is-amazon-cloudwatch)
  - [⚙️ 2. Prerequisites](#️-2-prerequisites)
  - [🏁 3. Getting Started — Console Overview](#-3-getting-started--console-overview)
  - [📊 4. Viewing AWS Metrics](#-4-viewing-aws-metrics)
    - [Example: EC2 instance metrics](#example-ec2-instance-metrics)
  - [🧱 5. Creating a Dashboard](#-5-creating-a-dashboard)
    - [Example: EC2 CPU Utilization Dashboard](#example-ec2-cpu-utilization-dashboard)
  - [🔔 6. Setting Up an Alarm](#-6-setting-up-an-alarm)
    - [Example: Alert when EC2 CPU \> 80% for 5 minutes](#example-alert-when-ec2-cpu--80-for-5-minutes)
  - [🧾 7. Monitoring Logs](#-7-monitoring-logs)
    - [Example: Sending logs from EC2](#example-sending-logs-from-ec2)
  - [🧩 8. Creating Custom Metrics](#-8-creating-custom-metrics)
    - [Example: Using AWS CLI](#example-using-aws-cli)
  - [⚡ 9. Automating with Events (CloudWatch Events / EventBridge)](#-9-automating-with-events-cloudwatch-events--eventbridge)
    - [Example: Restart EC2 on stop event](#example-restart-ec2-on-stop-event)
  - [🧠 10. Tips \& Best Practices](#-10-tips--best-practices)
  - [🚀 11. Optional: Programmatic Access (Node.js Example)](#-11-optional-programmatic-access-nodejs-example)
  - [📘 Summary](#-summary)
  - [References](#references)

Here’s a **step-by-step tutorial** to help you get started with **Amazon CloudWatch**, AWS’s monitoring and observability service. This guide will walk you through **key concepts**, **setup**, and **hands-on examples** of collecting, visualizing, and alerting on metrics and logs.

---

## 🧭 1. What Is Amazon CloudWatch?

**Amazon CloudWatch** is a monitoring and observability service that collects and tracks:

* **Metrics** (CPU, memory, latency, etc.)
* **Logs** (application/system logs)
* **Events** (state changes or scheduled triggers)
* **Traces** (if integrated with AWS X-Ray)

You can use CloudWatch to:

* Monitor AWS services and custom applications
* Set **alarms** for anomalies
* Visualize data in **dashboards**
* Automate responses to events

---

## ⚙️ 2. Prerequisites

* An **AWS account** with IAM permissions to access CloudWatch.
* **AWS CLI** or **AWS SDK** (optional, for CLI/programmatic examples).
* Optionally, **an EC2 instance**, **Lambda**, or an application emitting logs/metrics.

---

## 🏁 3. Getting Started — Console Overview

Go to the AWS Console → **CloudWatch**.

You’ll see five main sections:

1. **Dashboards** – visual charts for metrics.
2. **Metrics** – raw performance data from AWS services.
3. **Logs** – centralized log storage and search.
4. **Alarms** – automatic notifications/actions based on metric thresholds.
5. **Events / Rules** – automation for scheduled or event-driven workflows.

---

## 📊 4. Viewing AWS Metrics

AWS services automatically publish metrics to CloudWatch.

### Example: EC2 instance metrics

1. In the CloudWatch console → **Metrics** → **All Metrics**.
2. Choose **EC2** → **Per-Instance Metrics**.
3. Select your instance.
4. Choose metrics like:

   * `CPUUtilization`
   * `NetworkIn`, `NetworkOut`
   * `DiskReadBytes`, `DiskWriteBytes`

You can:

* Click **Add to dashboard** to visualize.
* Click **Add math expression** to combine metrics (e.g., average CPU).

---

## 🧱 5. Creating a Dashboard

### Example: EC2 CPU Utilization Dashboard

1. Go to **Dashboards → Create dashboard**.
2. Give it a name (e.g., `System-Monitoring`).
3. Add a **line widget**.
4. Select **EC2 → CPUUtilization**.
5. Click **Add to dashboard**.

You now have a live updating chart!

---

## 🔔 6. Setting Up an Alarm

### Example: Alert when EC2 CPU > 80% for 5 minutes

1. Go to **Alarms → All alarms → Create alarm**.
2. Choose a metric (e.g., `CPUUtilization`).
3. Set the condition:

   * Threshold: `>= 80`
   * Period: `5 minutes`
   * Consecutive datapoints: `1`
4. Define **actions**:

   * Send notification to **SNS topic** (e.g., email or Lambda).
5. Review and create.

Now CloudWatch will **notify you** when CPU exceeds 80%.

---

## 🧾 7. Monitoring Logs

CloudWatch Logs can collect and search your application/system logs.

### Example: Sending logs from EC2

1. Install the CloudWatch Agent:

   ```bash
   sudo yum install -y amazon-cloudwatch-agent
   ```
2. Configure it:

   ```bash
   sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
   ```
3. Start the agent:

   ```bash
   sudo systemctl start amazon-cloudwatch-agent
   ```

Logs will appear in **CloudWatch → Logs → Log groups**.

You can **filter**, **search**, or **create metrics from logs**.

---

## 🧩 8. Creating Custom Metrics

You can publish **custom application metrics** via the AWS CLI or SDK.

### Example: Using AWS CLI

```bash
aws cloudwatch put-metric-data \
  --metric-name "AppRequestCount" \
  --namespace "MyApp/Metrics" \
  --value 1 \
  --dimensions "Service=Auth"
```

Then view them in:
**CloudWatch → Metrics → Custom Namespaces → MyApp/Metrics**

---

## ⚡ 9. Automating with Events (CloudWatch Events / EventBridge)

You can trigger actions when AWS events occur.

### Example: Restart EC2 on stop event

1. Go to **Rules → Create rule**.
2. Event source: `Event pattern → EC2 → Instance state change → stopped`.
3. Target: Lambda function that starts the instance.
4. Save rule.

---

## 🧠 10. Tips & Best Practices

✅ Use **tags** to group metrics and resources.
✅ Create **composite alarms** to reduce alert noise.
✅ Use **CloudWatch Logs Insights** for SQL-like log queries.
✅ Use **Metric Math** to calculate derived values (e.g., `CPUUtilization / 2`).
✅ Set **retention policies** to manage log storage costs.

---

## 🚀 11. Optional: Programmatic Access (Node.js Example)

Install AWS SDK:

```bash
npm install aws-sdk
```

Send a custom metric:

```js
import AWS from "aws-sdk";
const cloudwatch = new AWS.CloudWatch();

cloudwatch.putMetricData({
  Namespace: "MyApp/Metrics",
  MetricData: [{
    MetricName: "Latency",
    Value: 120,
    Unit: "Milliseconds",
    Dimensions: [{ Name: "Endpoint", Value: "/login" }]
  }]
}).promise().then(() => console.log("Metric sent!"));
```

---

## 📘 Summary

| Feature            | Description                               |
| ------------------ | ----------------------------------------- |
| **Metrics**        | Track system & app performance            |
| **Dashboards**     | Visualize metrics in charts               |
| **Alarms**         | Notify when thresholds are exceeded       |
| **Logs**           | Store and analyze application/system logs |
| **Events/Rules**   | Automate actions on events                |
| **Custom Metrics** | Extend CloudWatch with app-specific data  |

---

## References

1. https://aws.amazon.com/pt/cloudwatch/
2. 