# Cloud

## [Azure](https://plantuml.com/stdlib)

```plantuml
@startuml
!include <azure/AzureCommon>
!include <azure/Analytics/AzureEventHub>
!include <azure/Analytics/AzureStreamAnalyticsJob>
!include <azure/Databases/AzureCosmosDb>

left to right direction

agent "Device Simulator" as devices #fff

AzureEventHub(fareDataEventHub, "Fare Data", "PK: Medallion HackLicense VendorId; 3 TUs")
AzureEventHub(tripDataEventHub, "Trip Data", "PK: Medallion HackLicense VendorId; 3 TUs")
AzureStreamAnalyticsJob(streamAnalytics, "Stream Processing", "6 SUs")
AzureCosmosDb(outputCosmosDb, "Output Database", "1,000 RUs")

devices --> fareDataEventHub
devices --> tripDataEventHub
fareDataEventHub --> streamAnalytics
tripDataEventHub --> streamAnalytics
streamAnalytics --> outputCosmosDb
@enduml
```

## AWS

```plantuml
@startuml
!include <awslib/AWSCommon>
!include <awslib/InternetOfThings/IoTRule>
!include <awslib/Analytics/KinesisDataStreams>
!include <awslib/ApplicationIntegration/SimpleQueueService>

left to right direction

agent "Published Event" as event #fff

IoTRule(iotRule, "Action Error Rule", "error if Kinesis fails")
KinesisDataStreams(eventStream, "IoT Events", "2 shards")
SimpleQueueService(errorQueue, "Rule Error Queue", "failed Rule actions")

event --> iotRule : JSON message
iotRule --> eventStream : messages
iotRule --> errorQueue : Failed action message
@enduml
```
```plantuml
@startuml
    !include <aws/common>
    !include <aws/Storage/AmazonS3/AmazonS3>
    !include <aws/Storage/AmazonS3/bucket/bucket>

    AMAZONS3(s3_internal)
    AMAZONS3(s3_partner,"Vendor's S3")
    s3_internal <- s3_partner
@enduml
```
## Google

```plantuml
@startuml
    !include <gcp/GCPCommon>
    !include <gcp/Compute/Cloud_Functions>
    !include <gcp/Networking/Cloud_Firewall_Rules>
    !include <gcp/Compute/Compute_Engine>
    !include <gcp/Storage/Cloud_Storage>

    Cloud_Functions(Cloud_FunctionsStart, "Start Server", "Cloud Functions")
    Cloud_Functions(Cloud_FunctionsStop, "Stop Server", "Cloud Functions")
    Cloud_Functions(Cloud_FunctionAdd, "Add a Friend", "Cloud Functions")
    Compute_Engine(Compute_Engine, "MineCraft Server", "Compute Engine")
    Cloud_Storage(Cloud_Storage, "MineCraft Backups", "Cloud Storage")
    Cloud_Firewall_Rules(Cloud_Firewall_Rules_Starter,"Minecraft Backups", "Cloud Firewall Rules")
    Cloud_Firewall_Rules(Cloud_Firewall_Rules_Friend,"Minecraft Backups", "Cloud Firewall Rules")
@enduml
```

## K8S

```plantuml
@startuml
    !include <k8s/Common>
    !include <k8s/Context>
    !include <k8s/Simplified>
    !include <k8s/OSS/all>
    footer Kubernetes Plant-UML
    scale max 1024 width
    skinparam {
        nodesep 10
        ranksep 10
    }
    actor "User" as userAlias
    left to right direction
    Cluster_Boundary(cluster, "Kubernetes Cluster") {
        Namespace_Boundary(ns, "Web") {
            KubernetesSvc(svc, "service", "")
            KubernetesPod(pod1, "web-pod1", "")
            KubernetesPod(pod2, "web-pod2", "")
        }
    }
    Rel(userAlias,svc,"get HTTP/1.1 index.html", "1")
    Rel(svc,pod1,"load Balances to Pods", "2")
    Rel(svc,pod2,"load Balances to Pods", "2")
    Rel_U(pod1, svc, "serves content", "3")
    Rel(svc, userAlias, "return content to", "4")
@enduml
```

## Mix with { }

```plantuml
@startuml
    !include <material/common>
    ' To import the sprite file you DON'T need to place a prefix!
    !include <material/folder_move>

    MA_FOLDER_MOVE(Red, 1, dir, rectangle, "A label") {

    }

    class foo {
        bar
    }

@enduml
``` 

## Elastic

```plantuml
@startuml
    !include <elastic/common>
    !include <elastic/elasticsearch/elasticsearch>
    !include <elastic/logstash/logstash>
    !include <elastic/kibana/kibana>

    ELASTICSEARCH(ElasticSearch, "Search and Analyze",database)
    LOGSTASH(Logstash, "Parse and Transform",node)
    KIBANA(Kibana, "Visualize",agent)

    Logstash -right-> ElasticSearch: Transformed Data
    ElasticSearch -right-> Kibana: Data to View

@enduml
```
## Cloudinsight PlantUML sprites

```plantuml
@startuml

!define SPRITESURL https://raw.githubusercontent.com/rabelenda/cicon-plantuml-sprites/v1.0/sprites
!includeurl SPRITESURL/tomcat.puml
!includeurl SPRITESURL/kafka.puml
!includeurl SPRITESURL/java.puml
!includeurl SPRITESURL/cassandra.puml

title Cloudinsight sprites example

skinparam monochrome true

rectangle "<$tomcat>\nwebapp" as webapp
queue "<$kafka>" as kafka
rectangle "<$java>\ndaemon" as daemon
database "<$cassandra>" as cassandra

webapp -> kafka
kafka -> daemon
daemon --> cassandra 

@enduml
```

## Archimate-PlantUML

```plantuml
@startuml
!includeurl https://raw.githubusercontent.com/ebbypeter/Archimate-PlantUML/master/Archimate.puml

title Archimate Sample - Requirement & Application Services

'Elements'
Motivation_Requirement(ReqPayrollStandard, "Do Payroll with a standard system")
Motivation_Requirement(ReqBudgetPlanning, "Do budget planning within the ERP system")

Application_Service(ASPayroll,"Payroll Service")
Application_Service(ASBudgetPlanning,"Budget Planning Service")
Application_Component(ACSAPFinanceAccRec, "SAP Finance - Accounts Recievables")
Application_Component(ACSAPHR, "SAP Human Resources")
Application_Component(ACSAPFin, "SAP Finance")
Application_Component(ACSAP,"SAP") 

'Relationships'
Rel_Realization_Up(ASPayroll, ReqPayrollStandard)
Rel_Realization_Up(ASBudgetPlanning, ReqBudgetPlanning)
Rel_Realization_Up(ACSAPFinanceAccRec, ASBudgetPlanning)
Rel_Realization_Up(ACSAPHR, ASPayroll)

Rel_Composition_Up(ACSAPFin, ACSAPFinanceAccRec)
Rel_Composition_Up(ACSAP, ACSAPHR)
Rel_Composition_Up(ACSAP, ACSAPFin)
@enduml
```

## EIP-PlantUML

```plantuml
rectangle "Business Object" as obj
component [Messaging\nInfrastructure] as infra
MessagingMapper(mapper, "Messaging Mapper") 
obj -- mapper
Send(mapper, infra)
```

## References

1. https://github.com/plantuml/plantuml-stdlib/tree/master
2. https://github.com/milo-minderbinder/AWS-PlantUML
3. https://github.com/awslabs/aws-icons-for-plantuml
4. https://github.com/plantuml-stdlib/Azure-PlantUML
5. https://github.com/awslabs/aws-icons-for-plantuml/blob/main/AWSSymbols.md
6. https://github.com/awslabs/aws-icons-for-plantuml
7. https://github.com/plantuml-stdlib/Azure-PlantUML/blob/master/AzureSymbols.md
8. https://github.com/plantuml-stdlib/plantuml-kubernetes-sprites
9. https://github.com/plantuml-stdlib/EIP-PlantUML
10. https://github.com/plantuml-stdlib/cicon-plantuml-sprites/blob/master/sprites-list.md
11. https://github.com/plantuml-stdlib/cicon-plantuml-sprites
12. 