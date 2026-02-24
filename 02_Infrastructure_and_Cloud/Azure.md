# Azure

## Diagram

```plantuml
@startuml
!pragma revision 1

!includeurl https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

!define AzurePuml https://raw.githubusercontent.com/plantuml-stdlib/Azure-PlantUML/master/dist
!includeurl AzurePuml/AzureCommon.puml
!includeurl AzurePuml/AzureC4Integration.puml
!includeurl AzurePuml/Databases/AzureRedisCache.puml
!includeurl AzurePuml/Databases/AzureCosmosDb.puml
!includeurl AzurePuml/Databases/AzureSqlDatabase.puml
!includeurl AzurePuml/Web/AzureWebApp.puml
!includeurl AzurePuml/Web/AzureCDN.puml
!includeurl AzurePuml/Web/AzureSearch.puml
!includeurl AzurePuml/Storage/AzureBlobStorage.puml
!includeurl AzurePuml/Storage/AzureQueueStorage.puml

LAYOUT_WITH_LEGEND()

Person(user, "User")

Container(spa, "Single-Page App", "Angular, JS")
AzureWebApp(webApp, "Web & API App", "ASP.NET Core MVC 2.1, C#", "Delivers the SPA and provides RESTful web APIs which are consumed from the SPA")
AzureCDN(cdn, "CDN", "Akamai S2", "caches publicly available content for lower latency and faster delivery of content")

AzureBlobStorage(staticBlobStorage, "Static Content", "General Purpose v2, Hot, LRS")

AzureQueueStorage(queue, "Queue", "General Purpose v2, LRS")
AzureSearch(search, "Search Index", "Standard S1", "provides search suggestions, fuzzy search, and language-specific search, consolidates a single search index from multiple data stores")
AzureRedisCache(redisCache, "Cache", "Standard C2")

AzureCosmosDb(cosmosDb, "Document DB", "SQL API, 400 RUs")
AzureSqlDatabase(sqlDb, "SQL DB", "Standard S3")

AzureWebApp(webJob, "Web Job", "WebJobs SDK v3, C#", "runs long-running tasks in the background")

Rel(user, spa, "Uses", "HTTPS")
Rel(user, webApp, "Uses", "HTTPS")
Rel(user, cdn, "Uses", "HTTPS")

Rel_Neighbor(spa, webApp, "Uses", "JSON, HTTPS")
Rel_Back_Neighbor(spa, webApp, "Delivers")

Rel_Neighbor(cdn, staticBlobStorage, "Reads from")

Rel(webApp, queue, "Puts background jobs into")
Rel(webApp, sqlDb, "Reads from and writes to", "ADO.NET")
Rel(webApp, cosmosDb, "Reads from and writes to", "SQL API")
Rel(webApp, redisCache, "Reads from and writes to")
Rel(webApp, search, "Reads from")

Rel_U(webJob, queue, "Gets next job from")
Rel_U(webJob, sqlDb, "Reads from and writes to", "ADO.NET")
Rel_U(webJob, cosmosDb, "Reads from and writes to", "SQL API")
Rel_U(webJob, redisCache, "Reads from and writes to")

Rel_Back_Neighbor(cosmosDb, search, "Builds index from")
Rel_Neighbor(search, sqlDb, "Builds index from")

Lay_D(search, webJob)

@enduml
```


```plantuml
@startuml Hello World
!pragma revision 1

!define AzurePuml https://raw.githubusercontent.com/plantuml-stdlib/Azure-PlantUML/master/dist
!includeurl AzurePuml/AzureCommon.puml
!includeurl AzurePuml/Databases/all.puml
!includeurl AzurePuml/Compute/AzureFunction.puml

actor "Person" as personAlias
AzureFunction(functionAlias, "Label", "Technology", "Optional Description")
AzureCosmosDb(cosmosDbAlias, "Label", "Technology", "Optional Description")

personAlias --> functionAlias
functionAlias --> cosmosDbAlias

@enduml
```

```plantuml

@startuml Raw usage - Sprites
!pragma revision 1

!define AzurePuml https://raw.githubusercontent.com/plantuml-stdlib/Azure-PlantUML/master/dist
!includeurl AzurePuml/AzureRaw.puml
!includeurl AzurePuml/Databases/AzureCosmosDb.puml
!includeurl AzurePuml/Compute/AzureFunction.puml


component "<color:red><$AzureFunction></color>" as myFunction

database "<color:#0072C6><$AzureCosmosDb></color>" as myCosmosDb

AzureFunction(mySecondFunction, "Stream Processing", "Consumption")

rectangle "<color:AZURE_SYMBOL_COLOR><$AzureCosmosDb></color>" as mySecondCosmosDb

myFunction --> myCosmosDb

mySecondFunction --> mySecondCosmosDb

@enduml
```

```plantuml
@startuml Two Mode Sample - Normal
!pragma revision 1

!define AzurePuml https://raw.githubusercontent.com/plantuml-stdlib/Azure-PlantUML/master/dist
!includeurl AzurePuml/AzureCommon.puml

' !includeurl AzurePuml/AzureSimplified.puml

!includeurl AzurePuml/Analytics/AzureEventHub.puml
!includeurl AzurePuml/Compute/AzureFunction.puml
!includeurl AzurePuml/Databases/AzureCosmosDb.puml
!includeurl AzurePuml/Storage/AzureDataLakeStorage.puml
!includeurl AzurePuml/Analytics/AzureStreamAnalyticsJob.puml
!includeurl AzurePuml/InternetOfThings/AzureTimeSeriesInsights.puml
!includeurl AzurePuml/Identity/AzureActiveDirectoryB2C.puml
!includeurl AzurePuml/DevOps/AzureApplicationInsights.puml


LAYOUT_LEFT_RIGHT

AzureEventHub(rawEventsHubAlias, "Raw Event Hub", "PK: Medallion HackLicense VendorId; 3 TUs")
AzureDataLakeStorage(datalakeAlias, "Data Lake", "GRS")
AzureStreamAnalyticsJob(streamAnalyticsAlias, "Aggregate Events", "6 SUs")
AzureFunction(stateFunctionAlias, "State Processor", "C#, Consumption Plan")
AzureEventHub(aggregatedEventsHubAlias, "Aggregated Hub", "6 TUs")
AzureCosmosDb(stateDBAlias, "State Database", "SQL API, 1000 RUs")
AzureTimeSeriesInsights(timeSeriesAlias, "Time Series", "2 Data Processing Units")

rawEventsHubAlias ----> datalakeAlias
rawEventsHubAlias --> streamAnalyticsAlias
rawEventsHubAlias ---> stateFunctionAlias
streamAnalyticsAlias --> aggregatedEventsHubAlias
aggregatedEventsHubAlias --> timeSeriesAlias
stateFunctionAlias --> stateDBAlias

@enduml
```


```plantuml
@startuml Two Mode Sample - Simplified
!pragma revision 1

!define AzurePuml https://raw.githubusercontent.com/plantuml-stdlib/Azure-PlantUML/master/dist
!includeurl AzurePuml/AzureCommon.puml

!includeurl AzurePuml/AzureSimplified.puml

!includeurl AzurePuml/Analytics/AzureEventHub.puml
!includeurl AzurePuml/Compute/AzureFunction.puml
!includeurl AzurePuml/Databases/AzureCosmosDb.puml
!includeurl AzurePuml/Storage/AzureDataLakeStorage.puml
!includeurl AzurePuml/Analytics/AzureStreamAnalyticsJob.puml
!includeurl AzurePuml/InternetOfThings/AzureTimeSeriesInsights.puml
!includeurl AzurePuml/Identity/AzureActiveDirectoryB2C.puml
!includeurl AzurePuml/DevOps/AzureApplicationInsights.puml


LAYOUT_LEFT_RIGHT

AzureEventHub(rawEventsHubAlias, "Raw Event Hub", "PK: Medallion HackLicense VendorId; 3 TUs")
AzureDataLakeStorage(datalakeAlias, "Data Lake", "GRS")
AzureStreamAnalyticsJob(streamAnalyticsAlias, "Aggregate Events", "6 SUs")
AzureFunction(stateFunctionAlias, "State Processor", "C#, Consumption Plan")
AzureEventHub(aggregatedEventsHubAlias, "Aggregated Hub", "6 TUs")
AzureCosmosDb(stateDBAlias, "State Database", "SQL API, 1000 RUs")
AzureTimeSeriesInsights(timeSeriesAlias, "Time Series", "2 Data Processing Units")

rawEventsHubAlias ----> datalakeAlias
rawEventsHubAlias --> streamAnalyticsAlias
rawEventsHubAlias ---> stateFunctionAlias
streamAnalyticsAlias --> aggregatedEventsHubAlias
aggregatedEventsHubAlias --> timeSeriesAlias
stateFunctionAlias --> stateDBAlias

@enduml
```

## Video
 * [Microsoft Azure Fundamentals Certification Course (AZ-900) UPDATED – Pass the exam in 8 hours!](https://www.youtube.com/watch?v=5abffC-K40c)
	> [<img src="https://img.youtube.com/vi/5abffC-K40c/0.jpg" width="200">](https://www.youtube.com/watch?v=5abffC-K40c "Microsoft Azure Fundamentals Certification Course (AZ-900) UPDATED – Pass the exam in 8 hours! by freeCodeCamp.org 257,301 views 8 hours, 21 minutes")

* [Azure AI Fundamentals Certification 2024 (AI-900) - Full Course to PASS the Exam](https://www.youtube.com/watch?v=hHjmr_YOqnU)
	> [<img src="https://img.youtube.com/vi/hHjmr_YOqnU/0.jpg" width="200">](https://www.youtube.com/watch?v=hHjmr_YOqnU "Prepare for the Azure AI Fundamentals Certification (AI-900) and pass! This course has been updated for 2024. by freeCodeCamp.org 69K views 4 hours, 23 minutes, 50 seconds")

 * [Deploy 12 apps to AWS, Azure, &amp; Google Cloud](https://www.youtube.com/watch?v=-ANCcFQBk6I)
	> [<img src="https://img.youtube.com/vi/-ANCcFQBk6I/0.jpg" width="200">](https://www.youtube.com/watch?v=-ANCcFQBk6I "Deploy 12 apps to AWS, Azure, &amp; Google Cloud by freeCodeCamp.org 103,767 views 1 hour, 37 minutes")

 * [Snowflake Architecture - Learn How Snowflake Stores Table data](https://www.youtube.com/watch?v=dxrEHqMFUWI)
	> [<img src="https://img.youtube.com/vi/dxrEHqMFUWI/0.jpg" width="200">](https://www.youtube.com/watch?v=dxrEHqMFUWI "Spark Programming and  Azure Databricks ILT Master Class by Prashant Kumar Pandey by Learning Journal 276K views 17 minutes, 05 seconds")

 * [Learn Terraform with Azure by Building a Dev Environment – Full Course for Beginners](https://www.youtube.com/watch?v=V53AHWun17s)
	> [<img src="https://img.youtube.com/vi/V53AHWun17s/0.jpg" width="200">](https://www.youtube.com/watch?v=V53AHWun17s "Learn Terraform with Azure by Building a Dev Environment – Full Course for Beginners by freeCodeCamp.org 166,031 views 1 hour, 38 minutes")

 * [Native VS Code Experience for Azure Databricks](https://www.youtube.com/watch?v=_QkcrYttVRs)
	> [<img src="https://img.youtube.com/vi/_QkcrYttVRs/0.jpg" width="200">](https://www.youtube.com/watch?v=_QkcrYttVRs "Native VS Code Experience for Azure Databricks by Databricks 4,762 views 1 minute, 57 seconds")
## References
1. https://learn.microsoft.com/en-us/azure/architecture/web-apps/app-service/architectures/baseline-zone-redundant
2. https://github.com/plantuml-stdlib/Azure-PlantUML/tree/master/samples
3. https://github.com/plantuml-stdlib/Azure-PlantUML#advanced-samples
4.  - Azure ML: https://lnkd.in/e5fvmvtk
5.  * [Sidecar pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/sidecar)
6.  * [Microservices Gateway](https://learn.microsoft.com/en-us/azure/architecture/microservices/design/gateway)
7.  https://learn.microsoft.com/en-us/azure/architecture/microservices/design/gateway
8.  https://learn.microsoft.com/en-us/training/azure/
9.  