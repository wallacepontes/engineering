# AWS Minimal CI/CD Diagram

## CI/CD Diagrams

```plantuml
@startuml CI/CD Workflow to AWS
!define AWSPuml https://raw.githubusercontent.com/awslabs/aws-icons-for-plantuml/v20.0/dist
!include AWSPuml/AWSCommon.puml

' Uncomment the following line to create simplified view
!include AWSPuml/AWSSimplified.puml

!include AWSPuml/General/Users.puml
!include AWSPuml/Compute/Lambda.puml
!include AWSPuml/NetworkingContentDelivery/APIGateway.puml
!include AWSPuml/Compute/EC2.puml
!include AWSPuml/Compute/EC2Instance.puml
!include AWSPuml/Groups/AWSCloud.puml
!include AWSPuml/Groups/VPC.puml
!include AWSPuml/Groups/AvailabilityZone.puml
' !include AWSPuml/Groups/PublicSubnet.puml
!include AWSPuml/Groups/PrivateSubnet.puml
!include AWSPuml/Groups/Region.puml
!include AWSPuml/NetworkingContentDelivery/VPCNATGateway.puml
!include AWSPuml/NetworkingContentDelivery/VPCInternetGateway.puml
!include AWSPuml/DeveloperTools/CodeBuild.puml
!include AWSPuml/Analytics/MSKAmazonMSKConnect.puml
!include AWSPuml/NetworkingContentDelivery/APIGateway.puml
!include AWSPuml/Storage/SimpleStorageService.puml

left to right direction 

hide stereotype

skinparam linetype ortho

Users(sources, "Git users", "millions of users")

MSKAmazonMSKConnect(3aParty,"Third-party\nGit repository","")

AWSCloudGroup(cloud) {
  RegionGroup(region) {   
    APIGateway(votingAPI, "Amazon API\nGateway", "user votes")
    VPCGroup(vpc) {
      PrivateSubnetGroup(az_1_private, "Private subnet") {
        Lambda(generateToken, "Lambda\nfunction", "return jwt") #Transparent
        
        CodeBuild(codeB, "AWS\nCodeBuild", "") #Transparent        
      }

    }
    SimpleStorageService(tes, "Amazon S3\noutput bucket","")
  }
}

sources --> 3aParty
3aParty --> votingAPI
votingAPI --> generateToken
generateToken --> codeB
codeB --> tes

```
