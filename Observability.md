# Observability

## Why Is DevOps Observability Important?

DevOps observability is crucial in ensuring the stability, reliability, and performance of modern software systems. Here are a few key reasons why:

1. Improved visibility: Observability provides real-time insights into the health, performance, and behavior of software systems. This helps teams quickly identify and resolve issues before they become major problems.

2. Faster problem resolution: By providing more detailed information about the inner workings of a system, observability helps DevOps teams quickly locate and fix issues.

3. Better collaboration: Observability enables DevOps teams to share relevant information and work together more effectively. For example, developers can use observability data to better understand how changes in their code are affecting the rest of the system, and operations teams can use it to monitor performance and proactively prevent problems.

4. Improved decision-making: Observability provides valuable data that can be used to make informed decisions about the design, deployment, and management of software systems.

5. Better customer experience: By providing real-time visibility into system behavior, observability can help DevOps teams deliver a better customer experience by quickly addressing performance and reliability issues.

In summary, DevOps observability is essential in today's fast-paced and complex software development environment, as it enables teams to quickly identify and resolve issues, improve collaboration, make informed decisions, and deliver a better customer experience.

## What are the 3 pillars of observability?

The three pillars of observability are metrics, logs, and traces. 

1. Metrics: Metrics are numerical values that represent the state or performance of a system at a given point in time. They provide a high-level overview of the health and behavior of a system and can be used to monitor key performance indicators (KPIs) and identify trends over time.

2. Logs: Logs provide a detailed record of events and actions that have taken place within a system. They capture data such as system messages, error messages, and debugging information, and provide valuable insights into the root cause of problems.

3. Traces: Traces provide a complete picture of a request or transaction as it moves through a system. They capture the sequence of events that occur, including the time taken for each step, and provide valuable insights into the performance and behavior of a system.

Together, these three pillars of observability provide a comprehensive view of a software system, allowing teams to monitor its behavior and performance, quickly identify and resolve issues, and improve overall reliability and user experience.

## Which clean architecture layer should we implement in microservices java for observability?

In a microservices architecture, observability is typically implemented at the infrastructure layer. This layer is responsible for providing the necessary infrastructure and tools for monitoring, logging, and tracing the behavior of the microservices.

For a Java-based microservices architecture, there are several open-source tools that can be used to implement observability, including:

1. Metrics: Micrometer, Dropwizard Metrics, or JMX

2. Logs: Log4j, Logback, or Java Util Logging

3. Traces: Zipkin, Jaeger, or OpenTracing

These tools can be integrated into the microservices infrastructure layer, where they can be used to collect, store, and analyze data about the behavior of the microservices. This data can then be used to provide real-time insights into the health, performance, and behavior of the system, as well as to quickly identify and resolve issues.

It's important to note that while observability is often implemented at the infrastructure layer, it's also possible to add observability capabilities at other layers of a microservices architecture, such as the application layer or the data layer, depending on the specific requirements of your system.

## Videos
 * [OpenTelemetry Course - Understand Software Performance](https://www.youtube.com/watch?v=r8UvWSX3KA8)
	> [<img src="https://img.youtube.com/vi/r8UvWSX3KA8/0.jpg" width="200">](https://www.youtube.com/watch?v=r8UvWSX3KA8 "OpenTelemetry Course - Understand Software Performance by freeCodeCamp.org 218,678 views 1 hour, 8 minutes")
 * [Introdução ao OpenTelemetry](https://www.youtube.com/watch?v=FBPKCoOp7Ss)
	> [<img src="https://img.youtube.com/vi/FBPKCoOp7Ss/0.jpg" width="200">](https://www.youtube.com/watch?v=FBPKCoOp7Ss "Introdução ao OpenTelemetry by Fabricio Veronez 6,520 views 1 hour, 24 minutes")
 * [Observability Explained with LogDNA](https://www.youtube.com/watch?v=bvVgP4tw_Hc)
	> [<img src="https://img.youtube.com/vi/bvVgP4tw_Hc/0.jpg" width="200">](https://www.youtube.com/watch?v=bvVgP4tw_Hc "Observability Explained with LogDNA by IBM Technology 19,989 views 8 minutes, 16 seconds")
 * [Observability vs. APM vs. Monitoring](https://www.youtube.com/watch?v=CAQ_a2-9UOI)
	> [<img src="https://img.youtube.com/vi/CAQ_a2-9UOI/0.jpg" width="200">](https://www.youtube.com/watch?v=CAQ_a2-9UOI "Observability vs. APM vs. Monitoring by IBM Technology 138,426 views 9 minutes, 41 seconds")
 * [Modern Observability with OpenTelemetry](https://www.youtube.com/watch?v=_OXYCzwFd1Y)
	> [<img src="https://img.youtube.com/vi/_OXYCzwFd1Y/0.jpg" width="200">](https://www.youtube.com/watch?v=_OXYCzwFd1Y "Modern Observability with OpenTelemetry by Lightstep is now ServiceNow Cloud Observability  17,879 views 11 minutes, 49 seconds")
 * [Observabilidade e Open Telemetry na Prática](https://www.youtube.com/watch?v=Y0gNpjHwx2M)
	> [<img src="https://img.youtube.com/vi/Y0gNpjHwx2M/0.jpg" width="200">](https://www.youtube.com/watch?v=Y0gNpjHwx2M "Observabilidade e Open Telemetry na Prática by Full Cycle 19,265 views 34 minutes")
 * [OpenTelemetry: Tudo o que você precisa saber para trabalhar com Observabilidade. #cortesfullcycle](https://www.youtube.com/watch?v=tKfummynBbg)
	> [<img src="https://img.youtube.com/vi/tKfummynBbg/0.jpg" width="200">](https://www.youtube.com/watch?v=tKfummynBbg "OpenTelemetry: Tudo o que você precisa saber para trabalhar com Observabilidade. #cortesfullcycle by Full Cycle 6,298 views 15 minutes")


## References

1. https://aws.amazon.com/pt/xray/
2. https://docs.datadoghq.com/tracing/trace_collection/open_standards/java/
3. https://docs.spring.io/spring-security/reference/reactive/integrations/observability.html
4. https://fission.io/blog/observability-with-opentelemetry-datadog-in-fission/
5. https://github.com/eugenp/tutorials/tree/master/spring-cloud-modules/spring-cloud-open-telemetry
6. https://github.com/muhammedsaidkaya/spring-otel-manual-instrumentation-demo/blob/master/demo-service/pom.xml
7. https://github.com/open-telemetry/opentelemetry-demo/
8. https://github.com/open-telemetry/opentelemetry-demo/tree/main/src
9. https://github.com/open-telemetry/opentelemetry-java-docs#java-opentelemetry-examples
10. https://github.com/open-telemetry/opentelemetry-java-instrumentation
11. https://github.com/open-telemetry/opentelemetry-java-instrumentation/issues/1534
12. https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases
13. https://github.com/open-telemetry/opentelemetry-java/blob/main/sdk-extensions/autoconfigure/README.md#prometheus-exporter
14. https://glowroot.org/
15. https://grafana.com/
16. https://grafana.com/blog/2022/04/26/set-up-and-observe-a-spring-boot-application-with-grafana-cloud-prometheus-and-opentelemetry/
17. https://grafana.com/docs/opentelemetry/

19. https://ish-ar.io/observability/
20. https://makimo.pl/blog/opentelemetry-integration-with-datadog/
21. https://newrelic.com/blog/best-practices/opentelemetry-intro-free-code-camp
22. https://newrelic.com/solutions/opentelemetry
23. https://opentelemetry.io/
24. https://opentelemetry.io/docs/collector/
25. https://opentelemetry.io/docs/collector/deployment/
26. https://opentelemetry.io/docs/collector/getting-started/
27. https://opentelemetry.io/docs/concepts/data-collection/
28. https://opentelemetry.io/docs/concepts/observability-primer/
29. https://opentelemetry.io/docs/instrumentation/
30. https://opentelemetry.io/docs/instrumentation/java/
31. https://opentelemetry.io/docs/instrumentation/java/automatic/annotations/
32. https://opentelemetry.io/docs/instrumentation/java/getting-started/
33. https://opentelemetry.io/docs/instrumentation/js/exporters/
34. https://opentracing.io/
35. https://prometheus.io/
36. https://signoz.io/blog/open-source-apm-tools/
37. https://signoz.io/blog/opentelemetry-vs-prometheus/
38. https://www.baeldung.com/spring-boot-actuators
39. https://www.baeldung.com/spring-boot-opentelemetry-setup
40. https://www.callicoder.com/spring-boot-actuator/
41. https://www.cncf.io/projects/fluentd/
42. https://www.cncf.io/projects/jaeger/
43. https://www.cncf.io/projects/opentelemetry/
44. https://www.cncf.io/projects/prometheus/
45. https://www.datadoghq.com/
46. https://www.ej-technologies.com/products/jprofiler/overview.html
47. https://www.elastic.co/guide/en/apm/guide/current/open-telemetry.html
48. https://www.elastic.co/pt/kibana/
49. https://www.elastic.co/pt/observability
50. https://www.honeycomb.io/
51. https://www.splunk.com/en_us/solutions/opentelemetry.html
52. https://zipkin.io/
53. https://devops.com/metrics-logs-and-traces-the-golden-triangle-of-observability-in-monitoring/