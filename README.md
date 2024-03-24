# Effulgencetech-aws-cicd-project
![CI/CD Pipeline architecture](https://github.com/Michaelgwei86/effulgencetech-aws-cicd/blob/main/effulgencetech-aws-cicd-demo.jpg)

### Infrastructure details
1. Consists of a VPC -----> 10.0.0.0/16
2. Consists of Two public subnets
    - Public subnet 1 ------> 10.0.0.0/24
    - Public subnet 2 ------> 10.0.1.0/24
3. Consists of Two private subnets
    - Private subnet 1 -----> 10.0.2.0/24
    - Private subnet 2 -----> 10.0.3.0/24
4. An Internet Gateway to the the VPC
5. A public route point to 0.0.0.0/0 attached to the Internet Gateway
6. Route table associations
7. NAT Gateway and NAT Gateway attachments
8. Application load balancer (ALB) components
    - ALB security group
    - ALB attachment to IGW
    - Target group
9. ECS Cluster
    - Cluster security group

## IAM Service Roles
- Autoscaling Role (Autoscaling role to verify the instance frequently and set u the autoscaling as required)
    - aws-cicd-demo-asg-role
- EC2 Role (For the EC2 instances to run ECS agent and register instances to ECS)
    - aws-cicd-ec2-role
- Task Execution Role ( Task execution role to pull images from ECR, push logs to CloudWatch)
- ECS Role (For ECS cluster to manage AWS resources)
    - aws-cicd-demo-ecs-role

## Fargate Service 
Deploy an ECS service on  AWS Fargate
- Service name ----> aws-cicd-demo-service
- Setup default Image from Dockerhub
- Specify container attributes
- Specify service count
- Create service resources
    - Log group for logs
    - Task definition
    - Service
    - Target group
    - Load balancer
