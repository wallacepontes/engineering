# Camunda & Workflow

## Camunda Modeler

Camunda Modeler is an open-source tool primarily used for modeling, designing, and editing BPMN (Business Process Model and Notation), DMN (Decision Model and Notation), and CMMN (Case Management Model and Notation) diagrams. These notations are standard graphical representations for business processes, decisions, and cases.

Here are some key features and functionalities of Camunda Modeler:

1. **BPMN, DMN, and CMMN Support**: Camunda Modeler provides support for creating and editing BPMN, DMN, and CMMN diagrams. Users can visually design their business processes, decision models, and case management scenarios using the respective notations.

2. **Graphical User Interface (GUI)**: The tool offers an intuitive and user-friendly graphical interface that allows users to easily drag and drop elements onto the canvas to create and modify their models.

3. **Element Library**: Camunda Modeler comes with a comprehensive library of BPMN, DMN, and CMMN elements, making it easy for users to select and add the necessary elements to their diagrams.

4. **Validation and Verification**: The tool provides validation and verification features to ensure that the created models adhere to the syntax and semantics defined by the BPMN, DMN, and CMMN standards.

5. **Integration with Camunda Platform**: Camunda Modeler seamlessly integrates with the Camunda platform, allowing users to import and export models to and from the Camunda BPM platform. This integration enables users to execute and monitor their business processes, decisions, and cases using Camunda's workflow automation capabilities.

6. **Extensibility**: Camunda Modeler is highly extensible, allowing users to customize and extend its functionality through plugins and extensions.

7. **Version Control Integration**: The tool supports integration with version control systems such as Git, enabling collaborative modeling and versioning of diagrams.

8. **Cross-Platform Compatibility**: Camunda Modeler is available for Windows, macOS, and Linux operating systems, ensuring compatibility across various platforms.

Overall, Camunda Modeler serves as a powerful tool for business analysts, process designers, and developers to visually model, analyze, and optimize their business processes, decisions, and cases.

## Differences between Camunda 8 and Camunda 7

According to the [Differences between Camunda 8 and Camunda 7](https://www.youtube.com/watch?v=GfBKjteDpD4), key differences between Camunda Platform 8 and Camunda 7 from a developer's perspective are:

### History

Camunda 7 has been three or 9 years, Camunda 8 is based on Camunda Cloud 1.4 ans was announced in April 2022.
Camunda 7 is guaranteed for additional 5 years. 
Camunda Platform 7 and 8 each contain a process engine at their core and can be used to automate BPMN processes.
Both products are very flexible, "developer-friendly" solutions, where software developers are involved in the process development (as opposed to so-called low-code suites).

### Differences

* Engine Architecture: 
	- Camunda 7 is based on a fork from **activity engine** 
	- Camunda 8 is based on a **Zeebe Engine** which is self developed.
		* Zeebe is scalable horizontally and linearly because of elactic search based backend instead dbms.

* Architecture and Task Processing: 
	- Camunda 7 has shared engine, embedded engine, remote engine and supports both synchronous and asynchronous task processing;
	- Camunda 8 only supports remote engine and asynchronous task processing.

* Communication Protocol: 
	- Camunda 7 uses REST API to talk to the engine whereas
	- Camunda 8 uses grpc protocol based gateways are used TaskList called cockpit in Camunda 7 now has GraphQL based APIs.

* Operating Options: 
	- Camunda 7 does not have a SaaS offering and only on-premise versions, while 
	- Camunda 8 provides SaaS and on premise versions which run on kubernetes clusters or development environment on Docker based containers, also Camunda 8 offers a more complex setup consisting of a larger number of components.
* Connectors: 
	- Camunda 7 offers pre-built connectors which can be placed directly in modular with only configurations and no code required. 
	- Camunda 8 offers a basic support for developing and operating your own connectors, but pre-built connectors are limited. Execution listeners are not available in Camunda 8.
* BPMN compliance: 
	- Camunda 7 offers full BPMN compliance, while 
	- Camunda 8 has restricted BPMN compliance but this is expected to improve over time.

Overall, Camunda 8 is a completely new platform compared to Camunda 7. It offers a different architecture, communication protocol, operating options, and feature set. Developers who are familiar with Camunda 7 will need to learn new things to work with Camunda 8.

## Airflow vs Camunda: What are the differences?
Airflow and Camunda are both popular workflow management systems. Let's explore the key differences between them.

1. **Execution Model:** One major difference between Airflow and Camunda lies in their execution models. Airflow follows a task-based execution model where tasks are defined and executed in a sequential manner. On the other hand, Camunda employs a process-based execution model where business processes are defined using BPMN (Business Process Model and Notation) and executed in a stateful manner. While Airflow is suitable for linear workflow execution, Camunda is designed for complex and dynamic process orchestration.

2. **Workflow Visualization:** Airflow provides a built-in UI for visualizing and monitoring workflows. It offers a graphical representation of the workflow structure and the status of each task. Camunda also offers a similar feature but with more advanced capabilities. Camunda provides a comprehensive process modeler that allows users to design, simulate, and visualize workflows in BPMN. Additionally, Camunda provides real-time monitoring and reporting features to track the execution progress of workflows.

3. **Task Scheduling:** Airflow has a built-in task scheduling mechanism that allows users to define dependencies between tasks and execute them based on certain conditions. Users can schedule tasks to run at specific times or intervals using cron-like expressions. Camunda, on the other hand, provides more advanced task scheduling capabilities. It supports time-based, event-based, and condition-based task triggers, providing more flexibility in defining task execution patterns.

4. **User Interaction and Forms:** Camunda excels in providing user interaction and form capabilities within workflows. It allows users to define user tasks with forms and gather input from users during the workflow execution. This makes Camunda suitable for scenarios where human interaction is required, such as approval processes or user task assignments. Airflow, on the other hand, does not have built-in support for user interaction and forms, focusing primarily on automated task execution.

5. **Integration and Extensibility:** Airflow provides a rich set of integrations and extensions, making it easy to connect with different systems and tools. It has a wide range of operators and hooks that enable integration with databases, cloud services, and various third-party tools. Camunda, being a comprehensive BPM platform, also offers extensive integration capabilities. It provides connectors and APIs to interact with other systems, databases, and services, making it suitable for enterprise workflow automation scenarios.

6. **Domain-Specific Features:** Each of these workflow management systems has certain domain-specific features that make them stand out. Airflow, being focused on data pipeline orchestration, provides built-in support for data processing tasks and integration with popular data processing frameworks like Apache Spark and Apache Hadoop. Camunda, with its BPMN-based approach, offers advanced capabilities for complex process modeling, decision management, and case management.

In summary, Airflow is a task-based data pipeline orchestration tool with basic workflow visualization and scheduling capabilities. On the other hand, Camunda is a comprehensive BPMN-based workflow and decision automation platform with advanced workflow modeling, user interaction, and extensibility features.


## Videos
 * [Ultimate Guide to Business Process Management (BPM) for Businesses](https://www.youtube.com/watch?v=JenVMTnJyzY)
	> [<img src="https://img.youtube.com/vi/JenVMTnJyzY/0.jpg" width="200">](https://www.youtube.com/watch?v=JenVMTnJyzY "Business processes are like the veins and arteries of an enterprise, keeping information flowing to keep the business alive. But, too many processes can harm a business's productivity and efficiency. Enter, business project management, or BPM. by Eye on Tech 393 views 10 minutes, 46 seconds")
 * [Avoid batch jobs! Model the future!](https://www.youtube.com/watch?v=oKq_ZsfrFfs)
	> [<img src="https://img.youtube.com/vi/oKq_ZsfrFfs/0.jpg" width="200">](https://www.youtube.com/watch?v=oKq_ZsfrFfs "Avoid batch jobs! Model the future! by CodeOpinion 13,712 views 53 minutes")
 * [Goodbye long procedural code! Fix it with workflows](https://www.youtube.com/watch?v=WjzojcyNp4U)
	> [<img src="https://img.youtube.com/vi/WjzojcyNp4U/0.jpg" width="200">](https://www.youtube.com/watch?v=WjzojcyNp4U "Goodbye long procedural code! Fix it with workflows by CodeOpinion 20,889 views 9 minutes, 5 seconds")
 * [#CamundaCon 2023: Bernd Ruecker Shares Why You Must Attend and Pack Your Running Shoes](https://www.youtube.com/watch?v=fNPHsQ-f8rE)
	> [<img src="https://img.youtube.com/vi/fNPHsQ-f8rE/0.jpg" width="200">](https://www.youtube.com/watch?v=fNPHsQ-f8rE "#CamundaCon 2023: Bernd Ruecker Shares Why You Must Attend and Pack Your Running Shoes by Camunda 369 views 2 minutes, 45 seconds")
 * [You&#39;re Invited to #CamundaCon 2023, the Process Orchestration Conference](https://www.youtube.com/watch?v=_DP99a9pSPQ)
	> [<img src="https://img.youtube.com/vi/_DP99a9pSPQ/0.jpg" width="200">](https://www.youtube.com/watch?v=_DP99a9pSPQ "You&#39;re Invited to #CamundaCon 2023, the Process Orchestration Conference by Camunda 1,262 views 33 seconds")
 * [Open Source: Camunda](https://www.youtube.com/watch?v=3Jfbrn6TXMk)
	> [<img src="https://img.youtube.com/vi/3Jfbrn6TXMk/0.jpg" width="200">](https://www.youtube.com/watch?v=3Jfbrn6TXMk "Open Source: Camunda by CockroachDB 307 views 52 minutes")
 * [Build Asynchronous Systems! The world is full of Asynchronous Workflows](https://www.youtube.com/watch?v=87fOMcRPDts)
	> [<img src="https://img.youtube.com/vi/87fOMcRPDts/0.jpg" width="200">](https://www.youtube.com/watch?v=87fOMcRPDts "Build Asynchronous Systems! The world is full of Asynchronous Workflows by CodeOpinion 7,100 views 11 minutes, 4 seconds")
 * [Workflow Orchestration for Building Resilient Software Systems](https://www.youtube.com/watch?v=hGiPWfWG8gs)
	> [<img src="https://img.youtube.com/vi/hGiPWfWG8gs/0.jpg" width="200">](https://www.youtube.com/watch?v=hGiPWfWG8gs "Workflow Orchestration for Building Resilient Software Systems by CodeOpinion 15,944 views 11 minutes, 57 seconds")
 * [The SAGA Design Pattern Explained in 6 MINUTES | Orchestration vs Choreography](https://www.youtube.com/watch?v=hkQhqDmriKA)
	> [<img src="https://img.youtube.com/vi/hkQhqDmriKA/0.jpg" width="200">](https://www.youtube.com/watch?v=hkQhqDmriKA "The SAGA Design Pattern Explained in 6 MINUTES | Orchestration vs Choreography by Marco Lenzo 11,286 views 6 minutes, 48 seconds")
 * [Udi Dahan - If (domain logic) then CQRS, or Saga?](https://www.youtube.com/watch?v=fWU8ZK0Dmxs)
	> [<img src="https://img.youtube.com/vi/fWU8ZK0Dmxs/0.jpg" width="200">](https://www.youtube.com/watch?v=fWU8ZK0Dmxs "Udi Dahan - If (domain logic) then CQRS, or Saga? by Domain-Driven Design Europe 36,941 views 46 minutes")
 * [ANÚNCIO OFICIAL !! NOVOS ATORES, TRAILER SAGA THE BATMAN E NOVIDADES WARNER E JAMES GUNN DCU](https://www.youtube.com/watch?v=EG-ZbmJsnlY)
	> [<img src="https://img.youtube.com/vi/EG-ZbmJsnlY/0.jpg" width="200">](https://www.youtube.com/watch?v=EG-ZbmJsnlY "ANÚNCIO OFICIAL !! NOVOS ATORES, TRAILER SAGA THE BATMAN E NOVIDADES WARNER E JAMES GUNN DCU by Hero Mania 73,172 views 13 minutes, 1 second")
 * [Descomplicando &quot;Sagas&quot;](https://www.youtube.com/watch?v=jMBfO52FttY)
	> [<img src="https://img.youtube.com/vi/jMBfO52FttY/0.jpg" width="200">](https://www.youtube.com/watch?v=jMBfO52FttY "Descomplicando &quot;Sagas&quot; by EximiaCo - Excelência Tecnológica  12,472 views 12 minutes, 45 seconds")
* [Differences between Camunda 8 and Camunda 7](https://www.youtube.com/watch?v=GfBKjteDpD4)
	> [<img src="https://img.youtube.com/vi/GfBKjteDpD4/0.jpg" width="200">](https://www.youtube.com/watch?v=GfBKjteDpD4 "Key differences between Camunda Platform 8 and Camunda 7 from a developers perspective by ETech Academy  696 views 3 minutes, 33 seconds")

## References

1. https://camunda.com/platform/
2. https://github.com/berndruecker/camunda-7-springboot-amqp-microservice-cloud-example
3. https://medium.com/@marcelloti/orquestra%C3%A7%C3%A3o-de-micro-servi%C3%A7os-com-zeebe-workflow-engine-bpmn-e-node-usando-nestjs-94621892170c
4. https://github.com/berndruecker/camunda-7-springboot-amqp-microservice-cloud-example
5. https://docs.camunda.io/docs/components/modeler/desktop-modeler/model-your-first-diagram/?_gl=1*yh5t7n*_ga*MjAxMzQ0MjE1OS4xNzEyNTE5MTcz*_ga_4EYN8X5FNR*MTcxMjUxOTE3Mi4xLjEuMTcxMjUxOTIwMi4zNC4wLjA.


