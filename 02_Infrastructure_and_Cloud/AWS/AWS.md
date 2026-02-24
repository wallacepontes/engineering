# AWS

```plantuml
@startuml
!define AWSPUML https://raw.githubusercontent.com/milo-minderbinder/AWS-PlantUML/release/18-2-22/dist

!includeurl AWSPUML/common.puml
!includeurl AWSPUML/ApplicationServices/AmazonAPIGateway/AmazonAPIGateway.puml
!includeurl AWSPUML/Compute/AWSLambda/AWSLambda.puml
!includeurl AWSPUML/Compute/AWSLambda/LambdaFunction/LambdaFunction.puml
!includeurl AWSPUML/Database/AmazonDynamoDB/AmazonDynamoDB.puml
!includeurl AWSPUML/Database/AmazonDynamoDB/table/table.puml
!includeurl AWSPUML/General/AWScloud/AWScloud.puml
!includeurl AWSPUML/General/client/client.puml
!includeurl AWSPUML/General/user/user.puml
!includeurl AWSPUML/SDKs/JavaScript/JavaScript.puml
!includeurl AWSPUML/Storage/AmazonS3/AmazonS3.puml
!includeurl AWSPUML/Storage/AmazonS3/bucket/bucket.puml


skinparam componentArrowColor Black
skinparam componentBackgroundColor White
skinparam nodeBackgroundColor White
skinparam agentBackgroundColor White
skinparam artifactBackgroundColor White


USER(user)
CLIENT(browser)
JAVASCRIPT(js,SDK)

AWSCLOUD(aws) {

    AMAZONS3(s3) {
        BUCKET(site,www.insecurity.co)
        BUCKET(logs,logs.insecurity.co)
    }

    AMAZONAPIGATEWAY(api)

    AWSLAMBDA(lambda) {
        LAMBDAFUNCTION(addComments,addComments)
    }

    AMAZONDYNAMODB(dynamo) {
        TABLE(comments,Comments)
    }
}

user - browser

browser -d-> site :**1a**) get\nstatic\ncontent
site ~> logs :1a
site .u.> browser :**1b**
browser - js
js -r-> comments :**2a**) get\ncomments
comments ..> js :**2b**

js -r-> api :**3**) add\ncomment

api -d-> addComments :**4**

addComments -> comments :**5**

comments ..> js :**6**) new\ncomments
@enduml
```

```plantuml
@startuml

!define AWSPUML https://raw.githubusercontent.com/milo-minderbinder/AWS-PlantUML/release/17-10-18/dist

!includeurl AWSPUML/common.puml
!includeurl AWSPUML/Storage/AmazonS3/AmazonS3.puml
!includeurl AWSPUML/Storage/AmazonS3/AmazonS3_LARGE.puml

skinparam nodeBackgroundColor White
skinparam storage<<**AmazonS3**>> {
    backgroundColor #F9DFDC
}
AMAZONS3(s3_internal,"Default S3")
AMAZONS3(s3_internal2,"S3 as node",node)
AMAZONS3_LARGE(s3_partner,"Large S3")

s3_internal2 <-r- s3_partner
s3_internal <-l- s3_partner

@enduml

```

```plantuml
@startuml

!define AWSPUML https://raw.githubusercontent.com/milo-minderbinder/AWS-PlantUML/release/17-10-18/dist

!includeurl AWSPUML/common.puml
!includeurl AWSPUML/Storage/AmazonS3/AmazonS3.puml
!includeurl AWSPUML/Storage/AmazonS3/bucket/bucket.puml


AMAZONS3(s3) {
    BUCKET(site,www.insecurity.co)
    BUCKET(logs,logs.insecurity.co)
}

site .r.> logs : events

@enduml
```

```plantuml

@startuml

!define AWSPUML https://raw.githubusercontent.com/milo-minderbinder/AWS-PlantUML/release/17-10-18/dist

!includeurl AWSPUML/common.puml
!includeurl AWSPUML/Storage/AmazonS3/AmazonS3.puml

AMAZONS3(s3_internal)
AMAZONS3(s3_partner,"Vendor's S3")

s3_internal <-- s3_partner

@enduml
```


## Videos

 * [AWS for Startups - Deploying with AWS Tutorial](https://www.youtube.com/watch?v=U3VSJhaC4kc)
	> [<img src="https://img.youtube.com/vi/U3VSJhaC4kc/0.jpg" width="200">](https://www.youtube.com/watch?v=U3VSJhaC4kc "AWS for Startups - Deploying with AWS Tutorial by freeCodeCamp.org 100,122 views 4 hours, 4 minutes")
 * [Terraform Course - Automate your AWS cloud infrastructure](https://www.youtube.com/watch?v=SLB_c_ayRMo)
	> [<img src="https://img.youtube.com/vi/SLB_c_ayRMo/0.jpg" width="200">](https://www.youtube.com/watch?v=SLB_c_ayRMo "Terraform Course - Automate your AWS cloud infrastructure by freeCodeCamp.org 1,833,366 views 2 hours, 20 minutes")
 * [Top AWS Services For Backend Developers](https://www.youtube.com/watch?v=UxIpAuIaV1E)
	> [<img src="https://img.youtube.com/vi/UxIpAuIaV1E/0.jpg" width="200">](https://www.youtube.com/watch?v=UxIpAuIaV1E "Top AWS Services For Backend Developers by Be A Better Dev 7,118 views 37 minutes")
 * [Como criar o seu primeiro fluxo de CI/CD na AWS (do zero com projeto em Node, React e Docker)](https://www.youtube.com/watch?v=O2TbkEhpfBE)
	> [<img src="https://img.youtube.com/vi/O2TbkEhpfBE/0.jpg" width="200">](https://www.youtube.com/watch?v=O2TbkEhpfBE "Como criar o seu primeiro fluxo de CI/CD na AWS (do zero com projeto em Node, React e Docker) by Domine AWS com Henrylle Maia 6,349 views 25 minutes")
 * [Code along - I built Vercel in 4 Hours (System Design, AWS, Redis, S3)](https://www.youtube.com/watch?v=c8_tafixiAs)
	> [<img src="https://img.youtube.com/vi/c8_tafixiAs/0.jpg" width="200">](https://www.youtube.com/watch?v=c8_tafixiAs "Code along - I built Vercel in 4 Hours (System Design, AWS, Redis, S3) by Harkirat Singh 233,903 views 2 hours, 37 minutes")
 * [Local Clusters for Amazon EKS on AWS Outposts](https://www.youtube.com/watch?v=zxTSKtQkF2M)
	> [<img src="https://img.youtube.com/vi/zxTSKtQkF2M/0.jpg" width="200">](https://www.youtube.com/watch?v=zxTSKtQkF2M "Local Clusters for Amazon EKS on AWS Outposts by Containers from the Couch 2,423 views 3 minutes, 30 seconds")
 * [Amazon EKS Anywhere vs EKS on AWS Outposts](https://www.youtube.com/watch?v=66yOdq2kXBA)
	> [<img src="https://img.youtube.com/vi/66yOdq2kXBA/0.jpg" width="200">](https://www.youtube.com/watch?v=66yOdq2kXBA "Amazon EKS Anywhere vs EKS on AWS Outposts by Containers from the Couch 5,271 views 10 minutes, 41 seconds")
 * [AWS Controllers for Kubernetes (ACK) Explained](https://www.youtube.com/watch?v=ZRMBnPwYP6k)
	> [<img src="https://img.youtube.com/vi/ZRMBnPwYP6k/0.jpg" width="200">](https://www.youtube.com/watch?v=ZRMBnPwYP6k "AWS Controllers for Kubernetes (ACK) Explained by Containers from the Couch 4,952 views 7 minutes, 42 seconds")
 * [AWS Certified Cloud Practitioner COMPLETE STUDY GUIDE - 2024](https://www.youtube.com/watch?v=JsmhEgIV1mQ)
	> [<img src="https://img.youtube.com/vi/JsmhEgIV1mQ/0.jpg" width="200">](https://www.youtube.com/watch?v=JsmhEgIV1mQ "AWS Certified Cloud Practitioner COMPLETE STUDY GUIDE - 2024 by Learn2Cloud1017 95,654 views 2 hours, 58 minutes")
 * [Event Driven Architectures vs Workflows (with AWS Services!)](https://www.youtube.com/watch?v=Q_QCu6OP2mQ)
	> [<img src="https://img.youtube.com/vi/Q_QCu6OP2mQ/0.jpg" width="200">](https://www.youtube.com/watch?v=Q_QCu6OP2mQ "Event Driven Architectures vs Workflows (with AWS Services!) by Be A Better Dev 84,006 views 15 minutes")
 * [Webinar: Instâncias de Leilão AWS: Tudo o que você precisa Saber!](https://www.youtube.com/watch?v=DZdeIb33iXY)
	> [<img src="https://img.youtube.com/vi/DZdeIb33iXY/0.jpg" width="200">](https://www.youtube.com/watch?v=DZdeIb33iXY "Webinar: Instâncias de Leilão AWS: Tudo o que você precisa Saber! by WR CONSULTORIA EM TI 95 views 1 hour, 51 minutes")
 * [Automating Security Controls Across Container Workloads With Snyk, Docker and AWS](https://www.youtube.com/watch?v=46klJ3Kt2BM)
	> [<img src="https://img.youtube.com/vi/46klJ3Kt2BM/0.jpg" width="200">](https://www.youtube.com/watch?v=46klJ3Kt2BM "Automating Security Controls Across Container Workloads With Snyk, Docker and AWS by Techstrong TV 307 views 46 minutes")
 * [FREE AWS Cloud Project Bootcamp (Week 4) - Relational Databases](https://www.youtube.com/watch?v=EtD7Kv5YCUs)
	> [<img src="https://img.youtube.com/vi/EtD7Kv5YCUs/0.jpg" width="200">](https://www.youtube.com/watch?v=EtD7Kv5YCUs "FREE AWS Cloud Project Bootcamp (Week 4) - Relational Databases by ExamPro 5,993 views 1 hour, 58 minutes")
 * [ChatGPT Tutorial for Developers - 10X your AWS Cloud Skills](https://www.youtube.com/watch?v=5E40Hut4CSo)
	> [<img src="https://img.youtube.com/vi/5E40Hut4CSo/0.jpg" width="200">](https://www.youtube.com/watch?v=5E40Hut4CSo "ChatGPT Tutorial for Developers - 10X your AWS Cloud Skills by Cloud Security Podcast 983 views 21 minutes")
 * [Deploy 12 apps to AWS, Azure, &amp; Google Cloud](https://www.youtube.com/watch?v=-ANCcFQBk6I)
	> [<img src="https://img.youtube.com/vi/-ANCcFQBk6I/0.jpg" width="200">](https://www.youtube.com/watch?v=-ANCcFQBk6I "Deploy 12 apps to AWS, Azure, &amp; Google Cloud by freeCodeCamp.org 103,767 views 1 hour, 37 minutes")
 * [AWS VPC Beginner to Pro - Virtual Private Cloud Tutorial](https://www.youtube.com/watch?v=g2JOHLHh4rI)
	> [<img src="https://img.youtube.com/vi/g2JOHLHh4rI/0.jpg" width="200">](https://www.youtube.com/watch?v=g2JOHLHh4rI "AWS VPC Beginner to Pro - Virtual Private Cloud Tutorial by freeCodeCamp.org 581,916 views 2 hours, 11 minutes")
 * [AWS Certified Cloud Practitioner Certification Course (CLF-C01) - Pass the Exam!](https://www.youtube.com/watch?v=SOTamWNgDKc)
	> [<img src="https://img.youtube.com/vi/SOTamWNgDKc/0.jpg" width="200">](https://www.youtube.com/watch?v=SOTamWNgDKc "AWS Certified Cloud Practitioner Certification Course (CLF-C01) - Pass the Exam! by freeCodeCamp.org 3,285,295 views 13 hours")
 * [AWS Cloud Development Kit (CDK) Crash Course](https://www.youtube.com/watch?v=T-H4nJQyMig)
	> [<img src="https://img.youtube.com/vi/T-H4nJQyMig/0.jpg" width="200">](https://www.youtube.com/watch?v=T-H4nJQyMig "AWS Cloud Development Kit (CDK) Crash Course by freeCodeCamp.org 186,464 views 1 hour")
 * [Go and AWS - Code and Deploy a Serverless API](https://www.youtube.com/watch?v=zHcef4eHOc8)
	> [<img src="https://img.youtube.com/vi/zHcef4eHOc8/0.jpg" width="200">](https://www.youtube.com/watch?v=zHcef4eHOc8 "Go and AWS - Code and Deploy a Serverless API by freeCodeCamp.org 85,597 views 1 hour, 44 minutes")
 * [DevOps with GitLab CI Course - Build Pipelines and Deploy to AWS](https://www.youtube.com/watch?v=PGyhBwLyK2U)
	> [<img src="https://img.youtube.com/vi/PGyhBwLyK2U/0.jpg" width="200">](https://www.youtube.com/watch?v=PGyhBwLyK2U "DevOps with GitLab CI Course - Build Pipelines and Deploy to AWS by freeCodeCamp.org 525,966 views 4 hours, 56 minutes")
 * [Learn Terraform (and AWS) by Building a Dev Environment – Full Course for Beginners](https://www.youtube.com/watch?v=iRaai1IBlB0)
	> [<img src="https://img.youtube.com/vi/iRaai1IBlB0/0.jpg" width="200">](https://www.youtube.com/watch?v=iRaai1IBlB0 "Learn Terraform (and AWS) by Building a Dev Environment – Full Course for Beginners by freeCodeCamp.org 267,356 views 1 hour, 39 minutes")
 * [FREE AWS Cloud Project Bootcamp (Week 4) - Relational Databases](https://www.youtube.com/watch?v=EtD7Kv5YCUs)
	> [<img src="https://img.youtube.com/vi/EtD7Kv5YCUs/0.jpg" width="200">](https://www.youtube.com/watch?v=EtD7Kv5YCUs "FREE AWS Cloud Project Bootcamp (Week 4) - Relational Databases by ExamPro 5,993 views 1 hour, 58 minutes")
 * [FREE AWS Cloud Project Bootcamp (Week 3) - Decentralized Authenication](https://www.youtube.com/watch?v=9obl7rVgzJw)
	> [<img src="https://img.youtube.com/vi/9obl7rVgzJw/0.jpg" width="200">](https://www.youtube.com/watch?v=9obl7rVgzJw "FREE AWS Cloud Project Bootcamp (Week 3) - Decentralized Authenication by ExamPro 6,433 views 1 hour, 59 minutes")
 * [Welcome to the FREE AWS Cloud Project Bootcamp!](https://www.youtube.com/watch?v=8b8SvQHc4Pk)
	> [<img src="https://img.youtube.com/vi/8b8SvQHc4Pk/0.jpg" width="200">](https://www.youtube.com/watch?v=8b8SvQHc4Pk "Welcome to the FREE AWS Cloud Project Bootcamp! by ExamPro 27,456 views 2 minutes, 56 seconds")
 * [FREE AWS Cloud Project Bootcamp (Week 3) - Decentralized Authenication](https://www.youtube.com/watch?v=9obl7rVgzJw)
	> [<img src="https://img.youtube.com/vi/9obl7rVgzJw/0.jpg" width="200">](https://www.youtube.com/watch?v=9obl7rVgzJw "FREE AWS Cloud Project Bootcamp (Week 3) - Decentralized Authenication by ExamPro 6,433 views 1 hour, 59 minutes")
 * [FREE AWS Cloud Project Bootcamp (Week 2) - Distributed Tracing](https://www.youtube.com/watch?v=2GD9xCzRId4)
	> [<img src="https://img.youtube.com/vi/2GD9xCzRId4/0.jpg" width="200">](https://www.youtube.com/watch?v=2GD9xCzRId4 "FREE AWS Cloud Project Bootcamp (Week 2) - Distributed Tracing by ExamPro 8,722 views 2 hours, 5 minutes")
 * [FREE AWS Cloud Project Bootcamp - Week 1 — App Containerization](https://www.youtube.com/watch?v=zJnNe5Nv4tE)
	> [<img src="https://img.youtube.com/vi/zJnNe5Nv4tE/0.jpg" width="200">](https://www.youtube.com/watch?v=zJnNe5Nv4tE "FREE AWS Cloud Project Bootcamp - Week 1 — App Containerization by ExamPro 15,895 views 2 hours, 3 minutes")
 * [Welcome to the FREE AWS Cloud Project Bootcamp!](https://www.youtube.com/watch?v=8b8SvQHc4Pk)
	> [<img src="https://img.youtube.com/vi/8b8SvQHc4Pk/0.jpg" width="200">](https://www.youtube.com/watch?v=8b8SvQHc4Pk "Welcome to the FREE AWS Cloud Project Bootcamp! by ExamPro 27,456 views 2 minutes, 56 seconds")
 * [Free AWS Cloud Project Bootcamp - Week 0 - Billing and Architecture](https://www.youtube.com/watch?v=SG8blanhAOg)
	> [<img src="https://img.youtube.com/vi/SG8blanhAOg/0.jpg" width="200">](https://www.youtube.com/watch?v=SG8blanhAOg "Free AWS Cloud Project Bootcamp - Week 0 - Billing and Architecture by ExamPro 26,378 views 2 hours, 2 minutes")
 * [FREE AWS Cloud Project Bootcamp - Update 2023-02-23](https://www.youtube.com/watch?v=gQxzMvk6BzM)
	> [<img src="https://img.youtube.com/vi/gQxzMvk6BzM/0.jpg" width="200">](https://www.youtube.com/watch?v=gQxzMvk6BzM "FREE AWS Cloud Project Bootcamp - Update 2023-02-23 by ExamPro 1,758 views 9 minutes, 20 seconds")
 * [The Best AWS Cloud Projects To Get You Hired (For Beginners)](https://www.youtube.com/watch?v=5RVT3BN9Iws)
	> [<img src="https://img.youtube.com/vi/5RVT3BN9Iws/0.jpg" width="200">](https://www.youtube.com/watch?v=5RVT3BN9Iws "The Best AWS Cloud Projects To Get You Hired (For Beginners) by Tech With Lucy 448,772 views 6 minutes, 17 seconds")
 * [FREE AWS Cloud Project Bootcamp Update - 2023-01-27](https://www.youtube.com/watch?v=dFkQI7wxc1w)
	> [<img src="https://img.youtube.com/vi/dFkQI7wxc1w/0.jpg" width="200">](https://www.youtube.com/watch?v=dFkQI7wxc1w "FREE AWS Cloud Project Bootcamp Update - 2023-01-27 by ExamPro 5,527 views 9 minutes, 46 seconds")
 * [O que é  TOGAF®? Pra que serve?](https://www.youtube.com/watch?v=AGy3zGnsaWs)
	> [<img src="https://img.youtube.com/vi/AGy3zGnsaWs/0.jpg" width="200">](https://www.youtube.com/watch?v=AGy3zGnsaWs "O que é  TOGAF®? Pra que serve? by eVOLVE Gestão Empresarial 2,216 views 2 minutes, 28 seconds")
 * [AWS Tutorial For Beginners | AWS Full Course🔥 | AWS Solutions Architect Certification | Simplilearn](https://www.youtube.com/watch?v=RLd_XTyt-w8)
	> [<img src="https://img.youtube.com/vi/RLd_XTyt-w8/0.jpg" width="200">](https://www.youtube.com/watch?v=RLd_XTyt-w8 "AWS Tutorial For Beginners | AWS Full Course🔥 | AWS Solutions Architect Certification | Simplilearn by Simplilearn 435,497 views 5 hours, 57 minutes")
 * [🔴 Build a Inspirational Quote Generator (AWS, NextJS, TypeScript, NodeJS) - 6 HOUR CLOUD PROJECT!](https://www.youtube.com/watch?v=XuCEi6SmIEo)
	> [<img src="https://img.youtube.com/vi/XuCEi6SmIEo/0.jpg" width="200">](https://www.youtube.com/watch?v=XuCEi6SmIEo "🔴 Build a Inspirational Quote Generator (AWS, NextJS, TypeScript, NodeJS) - 6 HOUR CLOUD PROJECT! by Brian H. Hough  |  Tech Stack Playbook 3,161 views 5 hours, 49 minutes")
 * [FREE AWS Cloud Project Bootcamp Update - 2023-02-05](https://www.youtube.com/watch?v=MxyxblAs2MQ)
	> [<img src="https://img.youtube.com/vi/MxyxblAs2MQ/0.jpg" width="200">](https://www.youtube.com/watch?v=MxyxblAs2MQ "FREE AWS Cloud Project Bootcamp Update - 2023-02-05 by ExamPro 3,596 views 18 minutes")
 * [FREE AWS Cloud Project Bootcamp Update (Repo Template and Teams) - 2023-02-07](https://www.youtube.com/watch?v=fQ55AORekc4)
	> [<img src="https://img.youtube.com/vi/fQ55AORekc4/0.jpg" width="200">](https://www.youtube.com/watch?v=fQ55AORekc4 "FREE AWS Cloud Project Bootcamp Update (Repo Template and Teams) - 2023-02-07 by ExamPro 2,838 views 10 minutes, 12 seconds")
 * [FREE AWS Cloud Project Bootcamp Update - 2023-02-05](https://www.youtube.com/watch?v=MxyxblAs2MQ)
	> [<img src="https://img.youtube.com/vi/MxyxblAs2MQ/0.jpg" width="200">](https://www.youtube.com/watch?v=MxyxblAs2MQ "FREE AWS Cloud Project Bootcamp Update - 2023-02-05 by ExamPro 3,596 views 18 minutes")
 * [AWS for Startups - Deploying with AWS Tutorial](https://www.youtube.com/watch?v=U3VSJhaC4kc)
	> [<img src="https://img.youtube.com/vi/U3VSJhaC4kc/0.jpg" width="200">](https://www.youtube.com/watch?v=U3VSJhaC4kc "AWS for Startups - Deploying with AWS Tutorial by freeCodeCamp.org 100,122 views 4 hours, 4 minutes")
 * [FREE AWS Cloud Project Bootcamp Update (Registry Report)- 2023-01-28](https://www.youtube.com/watch?v=S8EhM1VvI0c)
	> [<img src="https://img.youtube.com/vi/S8EhM1VvI0c/0.jpg" width="200">](https://www.youtube.com/watch?v=S8EhM1VvI0c "FREE AWS Cloud Project Bootcamp Update (Registry Report)- 2023-01-28 by ExamPro 6,347 views 33 minutes")
 * [FREE AWS Cloud Project Bootcamp Update - 2023-01-27](https://www.youtube.com/watch?v=dFkQI7wxc1w)
	> [<img src="https://img.youtube.com/vi/dFkQI7wxc1w/0.jpg" width="200">](https://www.youtube.com/watch?v=dFkQI7wxc1w "FREE AWS Cloud Project Bootcamp Update - 2023-01-27 by ExamPro 5,527 views 9 minutes, 46 seconds")
 * [DevOps with GitLab CI Course - Build Pipelines and Deploy to AWS](https://www.youtube.com/watch?v=PGyhBwLyK2U)
	> [<img src="https://img.youtube.com/vi/PGyhBwLyK2U/0.jpg" width="200">](https://www.youtube.com/watch?v=PGyhBwLyK2U "DevOps with GitLab CI Course - Build Pipelines and Deploy to AWS by freeCodeCamp.org 525,966 views 4 hours, 56 minutes")
 * [How to use ChatGPT to create Cloud Solutions on AWS](https://www.youtube.com/watch?v=XBdoMGTIVls)
	> [<img src="https://img.youtube.com/vi/XBdoMGTIVls/0.jpg" width="200">](https://www.youtube.com/watch?v=XBdoMGTIVls "How to use ChatGPT to create Cloud Solutions on AWS by Litwire 8,009 views 7 minutes, 3 seconds")
 * [AWS Certified Solutions Architect - Associate 2020 (PASS THE EXAM!)](https://www.youtube.com/watch?v=Ia-UEYYR44s)
	> [<img src="https://img.youtube.com/vi/Ia-UEYYR44s/0.jpg" width="200">](https://www.youtube.com/watch?v=Ia-UEYYR44s "AWS Certified Solutions Architect - Associate 2020 (PASS THE EXAM!) by freeCodeCamp.org 2,972,947 views 10 hours, 26 minutes")
 * [AWS Certified Solutions Architect Associate 2023 | Learn AWS Free | AWS Full Crash Course](https://www.youtube.com/watch?v=uc5C1Zt5tD8)
	> [<img src="https://img.youtube.com/vi/uc5C1Zt5tD8/0.jpg" width="200">](https://www.youtube.com/watch?v=uc5C1Zt5tD8 "AWS Certified Solutions Architect Associate 2023 | Learn AWS Free | AWS Full Crash Course by Go Cloud Architects 152,295 views 10 hours, 10 minutes")
 * [AWS Certified Developer - Associate 2020 (PASS THE EXAM!)](https://www.youtube.com/watch?v=RrKRN9zRBWs)
	> [<img src="https://img.youtube.com/vi/RrKRN9zRBWs/0.jpg" width="200">](https://www.youtube.com/watch?v=RrKRN9zRBWs "AWS Certified Developer - Associate 2020 (PASS THE EXAM!) by freeCodeCamp.org 1,057,415 views 11 hours, 58 minutes")
 * [AWS Certified Cloud Practitioner Training 2020 - Full Course](https://www.youtube.com/watch?v=3hLmDS179YE)
	> [<img src="https://img.youtube.com/vi/3hLmDS179YE/0.jpg" width="200">](https://www.youtube.com/watch?v=3hLmDS179YE "AWS Certified Cloud Practitioner Training 2020 - Full Course by freeCodeCamp.org 4,283,544 views 3 hours, 58 minutes")
 * [Why you should avoid AWS Exam Dumps](https://www.youtube.com/watch?v=cj4MbTFTqQM)
	> [<img src="https://img.youtube.com/vi/cj4MbTFTqQM/0.jpg" width="200">](https://www.youtube.com/watch?v=cj4MbTFTqQM "Why you should avoid AWS Exam Dumps by Digital Cloud Training 11,102 views 3 minutes, 58 seconds")
 * [AWS Certified Cloud Practitioner Certification Course (CLF-C01) - Pass the Exam!](https://www.youtube.com/watch?v=SOTamWNgDKc)
	> [<img src="https://img.youtube.com/vi/SOTamWNgDKc/0.jpg" width="200">](https://www.youtube.com/watch?v=SOTamWNgDKc "AWS Certified Cloud Practitioner Certification Course (CLF-C01) - Pass the Exam! by freeCodeCamp.org 3,285,295 views 13 hours")
 * [AWS for Startups - Deploying with AWS Tutorial](https://www.youtube.com/watch?v=U3VSJhaC4kc)
	> [<img src="https://img.youtube.com/vi/U3VSJhaC4kc/0.jpg" width="200">](https://www.youtube.com/watch?v=U3VSJhaC4kc "AWS for Startups - Deploying with AWS Tutorial by freeCodeCamp.org 100,122 views 4 hours, 4 minutes")
 * [AWS Certified Solutions Architect - Associate 2020 (PASS THE EXAM!)](https://www.youtube.com/watch?v=Ia-UEYYR44s)
	> [<img src="https://img.youtube.com/vi/Ia-UEYYR44s/0.jpg" width="200">](https://www.youtube.com/watch?v=Ia-UEYYR44s "AWS Certified Solutions Architect - Associate 2020 (PASS THE EXAM!) by freeCodeCamp.org 2,972,947 views 10 hours, 26 minutes")
 * [AWS Certified Developer - Associate 2020 (PASS THE EXAM!)](https://www.youtube.com/watch?v=RrKRN9zRBWs)
	> [<img src="https://img.youtube.com/vi/RrKRN9zRBWs/0.jpg" width="200">](https://www.youtube.com/watch?v=RrKRN9zRBWs "AWS Certified Developer - Associate 2020 (PASS THE EXAM!) by freeCodeCamp.org 1,057,415 views 11 hours, 58 minutes")
 * [AWS for Startups - Deploying with AWS Tutorial](https://www.youtube.com/watch?v=U3VSJhaC4kc)
	> [<img src="https://img.youtube.com/vi/U3VSJhaC4kc/0.jpg" width="200">](https://www.youtube.com/watch?v=U3VSJhaC4kc "AWS for Startups - Deploying with AWS Tutorial by freeCodeCamp.org 100,122 views 4 hours, 4 minutes")
 * [AWS Certified Cloud Practitioner Training 2020 - Full Course](https://www.youtube.com/watch?v=3hLmDS179YE)
	> [<img src="https://img.youtube.com/vi/3hLmDS179YE/0.jpg" width="200">](https://www.youtube.com/watch?v=3hLmDS179YE "AWS Certified Cloud Practitioner Training 2020 - Full Course by freeCodeCamp.org 4,283,544 views 3 hours, 58 minutes")

## References
1. https://github.com/milo-minderbinder/AWS-PlantUML
2. https://github.com/milo-minderbinder/AWS-PlantUML/blob/master/examples
3. https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html
4. https://docs.aws.amazon.com/
5. https://docs.aws.amazon.com/ec2/latest/devguide/ec2-endpoints.html
6. https://athenaframework.com/
7. 