# AWS ECS Fargate

ECS Fargate is a serverless option for running Docker containers on AWS without managing the underlying servers. ECS is the container orchestration service, while Fargate is a "launch type" within ECS that handles the server infrastructure automatically. You provide your container image, define the CPU and memory needed, and Fargate provisions and scales the necessary compute resources for you.

## Table of Contents

- [AWS ECS Fargate](#aws-ecs-fargate)
  - [Table of Contents](#table-of-contents)
  - [How it works](#how-it-works)
  - [Key difference from ECS on EC2](#key-difference-from-ecs-on-ec2)
  - [References](#references)

## How it works

- Container orchestration with ECS: Amazon ECS is the service that manages your containerized applications, defining how they run.
- Serverless compute with Fargate: With the Fargate launch type, you don't need to provision or manage EC2 instances. Fargate automatically handles the provisioning and scaling of the compute resources.
- Defining your application: You package your application in a Docker container, create an ECS Task Definition that specifies the container, CPU, and memory requirements, and then launch it as a task or service.
- Focus on your application: This approach allows you to focus on building and deploying your application rather than managing the underlying servers, patching, or capacity planning.
- Scaling: Fargate automatically scales your application based on your configuration, handling traffic fluctuations without manual intervention.
- Cost: You are charged for the vCPU, memory, and storage resources used by your containers, from the moment they start until they are terminated. 

## Key difference from ECS on EC2

- Fargate: A serverless option where AWS manages the infrastructure. You pay for the resources your containers use directly.
- ECS on EC2: An option where you manage a cluster of EC2 instances to run your containers. This gives you more control over the underlying infrastructure but requires more management.

## References

1. https://docs.aws.amazon.com/pt_br/AmazonECS/latest/developerguide/AWS_Fargate.html
2. https://medium.com/@matheus510.fonseca/aws-ecs-fargate-o-que-%C3%A9-devo-usar-no-meu-projeto-atual-576e6b45e92c
3. https://aws.amazon.com/pt/fargate/

