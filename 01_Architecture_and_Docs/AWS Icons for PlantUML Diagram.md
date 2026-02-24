# AWS Icons for PlantUML Diagram

## Table of Contents
- [AWS Icons for PlantUML Diagram](#aws-icons-for-plantuml-diagram)
  - [Table of Contents](#table-of-contents)
  - [Hello World](#hello-world)
  - [Basic Usage](#basic-usage)
  - [Raw Images](#raw-images)
  - [Simplified View](#simplified-view)
  - [Sequence Diagram](#sequence-diagram)
    - [Sequence Diagram - Technical](#sequence-diagram---technical)
    - [Sequence Diagram with lifelines](#sequence-diagram-with-lifelines)
  - [AWS Cloud - Virtual private cloud (VPC)](#aws-cloud---virtual-private-cloud-vpc)
  - [AWS CodePipeline](#aws-codepipeline)
  - [References](#references)

## Hello World

```plantuml
@startuml Hello World
' Uncomment the line below for "dark mode" styling
'!$AWS_DARK = true

!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
!include AWSPuml/AWSCommon.puml
!include AWSPuml/BusinessApplications/all.puml
!include AWSPuml/Storage/SimpleStorageService.puml

actor "Person" as personAlias
WorkDocs(desktopAlias, "Label", "Technology", "Optional Description")
SimpleStorageService(storageAlias, "Label", "Technology", "Optional Description")

personAlias --> desktopAlias
desktopAlias --> storageAlias

@enduml
```
## Basic Usage

```plantuml
@startuml Basic Usage - AWS IoT Rules Engine
' Uncomment the line below for "dark mode" styling
'!$AWS_DARK = true

!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
!include AWSPuml/AWSCommon.puml
!include AWSPuml/InternetOfThings/IoTRule.puml
!include AWSPuml/Analytics/KinesisDataStreams.puml
!include AWSPuml/ApplicationIntegration/SimpleQueueService.puml

left to right direction

agent "Published Event" as event

IoTRule(iotRule, "Action Error Rule", "error if Kinesis fails")
KinesisDataStreams(eventStream, "IoT Events", "2 shards")
SimpleQueueService(errorQueue, "Rule Error Queue", "failed Rule actions")

event --> iotRule : JSON message
iotRule --> eventStream : messages
iotRule --> errorQueue : Failed action message

@enduml
```

## Raw Images

```plantuml
@startuml Raw usage - Images
' Uncomment the line below for "dark mode" styling
'!$AWS_DARK = true

!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
!include AWSPuml/AWSCommon.puml
!include AWSPuml/ArtificialIntelligence/SageMakerModel.puml
!include AWSPuml/Robotics/RoboMaker.puml

component "$SageMakerModelIMG()" as myMLModel
database "$RoboMakerIMG()" as myRoboticService
RoboMaker(mySecondFunction, "Reinforcement Learning", "Gazebo")

rectangle "$SageMakerModelIMG()" as mySecondML

myMLModel --> myRoboticService
mySecondFunction --> mySecondML

@enduml
```

## Simplified View

```plantuml
@startuml Two Modes - Technical View
' Uncomment the line below for "dark mode" styling
'!$AWS_DARK = true

!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
!include AWSPuml/AWSCommon.puml

' Uncomment the following line to create simplified view
' !include AWSPuml/AWSSimplified.puml

!include AWSPuml/General/Users.puml
!include AWSPuml/NetworkingContentDelivery/APIGateway.puml
!include AWSPuml/SecurityIdentityCompliance/Cognito.puml
!include AWSPuml/Compute/Lambda.puml
!include AWSPuml/Database/DynamoDB.puml

left to right direction

Users(sources, "Events", "millions of users")
APIGateway(votingAPI, "Voting API", "user votes")
Cognito(userAuth, "User Authentication", "jwt to submit votes")
Lambda(generateToken, "User Credentials", "return jwt")
Lambda(recordVote, "Record Vote", "enter or update vote per user")
DynamoDB(voteDb, "Vote Database", "one entry per user")

sources --> userAuth
sources --> votingAPI
userAuth <--> generateToken
votingAPI --> recordVote
recordVote --> voteDb
@enduml
```

## Sequence Diagram

### Sequence Diagram - Technical

```plantuml
@startuml Sequence Diagram - Technical
' Uncomment the line below for "dark mode" styling
'!$AWS_DARK = true

!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
!include AWSPuml/AWSCommon.puml
!include AWSPuml/Compute/all.puml
!include AWSPuml/NetworkingContentDelivery/APIGateway.puml
!include AWSPuml/General/Internetalt1.puml
!include AWSPuml/Database/DynamoDB.puml

actor User as user
APIGatewayParticipant(api, Credit Card System, All methods are POST)
LambdaParticipant(lambda,AuthorizeCard,)
DynamoDBParticipant(db, PaymentTransactions, sortkey=transaction_id+token)
Internetalt1Participant(processor, Authorizer, Returns status and token)

user -> api: Process transaction\nPOST /prod/process
api -> lambda: Invokes lambda with cardholder details
lambda -> processor: Submit via API token\ncard number, expiry, CID
processor -> processor: Validate and create token
processor -> lambda: Returns status code and token
lambda -> db: PUT transaction id, token
lambda -> api: Returns\nstatus code, transaction id
api -> user: Returns status code
@enduml
```

### Sequence Diagram with lifelines

```plantuml
@startuml Sequence Diagram - Images
' Uncomment the line below for "dark mode" styling
'!$AWS_DARK = true

!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
!include AWSPuml/AWSCommon.puml
!include AWSPuml/AWSExperimental.puml
!include AWSPuml/Compute/Lambda.puml
!include AWSPuml/NetworkingContentDelivery/APIGateway.puml
!include AWSPuml/General/Internetalt1.puml
!include AWSPuml/General/User.puml
!include AWSPuml/General/AuthenticatedUser.puml
!include AWSPuml/Database/DynamoDB.puml

'Hide the bottom boxes / Use filled triangle arrowheads
hide footbox
skinparam style strictuml

skinparam MaxMessageSize 200

participant "$AuthenticatedUserIMG()\nUser" as user
box AWS Cloud
'Instead of using ...Participant(), native creole img tags can be used
participant "$APIGatewayIMG()\nCredit Card System\nAll methods are POST" as api << REST API >>
participant "$LambdaIMG()\nAuthorizeCard\nReturns status" as lambda << python3.9 >>
participant "PaymentTransactions\n$DynamoDBIMG()\nsortkey=transaction_id+token" as db << on-demand >>
endbox
participant "Authorizer\nReturns status and token\n$Internetalt1IMG()" as processor

'Use shortcut syntax for activation with colored lifelines and return keyword
user -> api++ $AWSColor(ApplicationIntegration): <$Callout_1> Process transaction\l<$Callout_SP> ""POST /prod/process""
api -> lambda++ $AWSColor(Compute): <$Callout_2> Invokes lambda with\l<$Callout_SP> cardholder details
lambda -> processor++ $AWS_COLOR_SQUID: <$Callout_3> Submit via API token\l<$Callout_SP> card number, expiry, CID
processor -> processor: Validate and\lcreate token
return status code, token
lambda ->> db: PUT transaction id, token
return status code,\rtransaction id
return status code
@enduml
```

## AWS Cloud - Virtual private cloud (VPC)

```plantuml
@startuml VPC
' Uncomment the line below for "dark mode" styling
'!$AWS_DARK = true

!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
!include AWSPuml/AWSCommon.puml
!include AWSPuml/AWSSimplified.puml
!include AWSPuml/Compute/EC2.puml
!include AWSPuml/Compute/EC2Instance.puml
!include AWSPuml/Groups/AWSCloud.puml
!include AWSPuml/Groups/VPC.puml
!include AWSPuml/Groups/AvailabilityZone.puml
!include AWSPuml/Groups/PublicSubnet.puml
!include AWSPuml/Groups/PrivateSubnet.puml
!include AWSPuml/NetworkingContentDelivery/VPCNATGateway.puml
!include AWSPuml/NetworkingContentDelivery/VPCInternetGateway.puml

hide stereotype
skinparam linetype ortho

AWSCloudGroup(cloud) {
  VPCGroup(vpc) {
    VPCInternetGateway(internet_gateway, "Internet gateway", "")

    AvailabilityZoneGroup(az_1, "\tAvailability Zone 1\t") {
      PublicSubnetGroup(az_1_public, "Public subnet") {
        VPCNATGateway(az_1_nat_gateway, "NAT gateway", "") #Transparent
      }
      PrivateSubnetGroup(az_1_private, "Private subnet") {
        EC2Instance(az_1_ec2_1, "Instance", "") #Transparent
      }

      az_1_ec2_1 .u.> az_1_nat_gateway
    }

    AvailabilityZoneGroup(az_2, "\tAvailability Zone 2\t") {
      PublicSubnetGroup(az_2_public, "Public subnet") {
        VPCNATGateway(az_2_nat_gateway, "NAT gateway", "") #Transparent
      }
      PrivateSubnetGroup(az_2_private, "Private subnet") {
        EC2Instance(az_2_ec2_1, "Instance", "") #Transparent
      }

      az_2_ec2_1 .u.> az_2_nat_gateway
    }

    az_2_nat_gateway .[hidden]u.> internet_gateway
    az_1_nat_gateway .[hidden]u.> internet_gateway
  }
}
@enduml
```
## AWS CodePipeline

```plantuml
@startuml AWS CodePipeline - Human Approval Step
' based on https://catalog.us-east-1.prod.workshops.aws/workshops/752fd04a-f7c3-49a0-a9a0-c9b5ed40061b/en-US/codepipeline-extend

' Uncomment the line below for "dark mode" styling
'!$AWS_DARK = true

!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
!include AWSPuml/AWSCommon.puml
!include AWSPuml/AWSExperimental.puml
!include AWSPuml/ApplicationIntegration/SimpleNotificationService.puml
!include AWSPuml/Compute/EC2.puml
!include AWSPuml/DeveloperTools/CodeBuild.puml
!include AWSPuml/DeveloperTools/CodeDeploy.puml
!include AWSPuml/DeveloperTools/CodePipeline.puml
!include AWSPuml/General/GitRepository.puml
!include AWSPuml/General/User.puml
!include AWSPuml/Storage/SimpleStorageService.puml

$AWSGroupColoring(CodePipelineGroup, $AWSColor(DeveloperTools))
!define CodePipelineGroup(g_alias, g_label="AWS CodePipeline") $AWSDefineGroup(g_alias, g_label, CodePipeline, CodePipelineGroup)

' Groups are rectangles with a custom style using stereotype - need to hide
hide stereotype
skinparam linetype ortho
skinparam rectangle {
    BackgroundColor $AWS_BG_COLOR
    BorderColor transparent
}

' define custom procedure for AWS Service icon and two lines of text
!procedure $AWSIcon($service, $line1, $line2="")
rectangle "$AWSImg($service)\n$line1\n$line2"
!endprocedure 

CodePipelineGroup(pipeline){
  $AWSIcon(GitRepository, "Git Repository") as gr
  $AWSIcon(CodeBuild, "AWS CodeBuild") as cb
  $AWSIcon(SimpleStorageService, "Amazon S3", "(artifact store)") as s3
  gr -r-> cb: \n<$Callout_1>
  cb -d-> s3: <$Callout_2><$Callout_SP>

  $AWSIcon(CodeDeploy, "AWS CodeDeploy") as cd1
  $AWSIcon(EC2, "Amazon EC2", "(dev)") as ec2dev
  cb -r-> cd1: \n<$Callout_3>
  cd1 -d-> ec2dev: <$Callout_4><$Callout_SP>

  $AWSIcon(User, "Human", "Approval") as user
  cd1 -r-> user: \n<$Callout_5>

  $AWSIcon(CodeDeploy, "AWS CodeDeploy") as cd2
  $AWSIcon(EC2, "Amazon EC2", "(prod)") as ec2prod
  user -r-> cd2: \n<$Callout_6>
  cd2 -d-> ec2prod: <$Callout_7><$Callout_SP>

  $AWSIcon(SimpleNotificationService, "SNS Notification") as sns
  cd2 -r-> sns: \n<$Callout_8>
}
@enduml
```


## References

1. https://github.com/awslabs/aws-icons-for-plantuml/
2. https://github.com/awslabs/aws-icons-for-plantuml/blob/main/AWSSymbols.md
3. https://github.com/plantuml/plantuml-stdlib
4. https://github.com/milo-minderbinder/AWS-PlantUML
5. https://github.com/plantuml-stdlib/Azure-PlantUML