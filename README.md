# AWS-ECS

AWS ECS (Elastic Container service) is used to run docker containers from a fully managed service<br/>without having to worry about provisioning of compute resources.<br/>



In this project I am creating an ECS cluster to run a Jenkins application, a docker image pulled from Dockerhub,<br/>& exposing it through an ALB to allow access to it.

<hr/>

## Prerequisites:

 - ALB (with port 80 listener open & target group listener on port 8080)
 - Jenkins Docker image URI found on Dockerhub:
   - ``` "jenkins/jenkins:lts-jdk11" ```
 - ecsTaskExecutionRole Role to allow ECS to run on your account (IAM Role as shown below with permission):

![image](https://github.com/Semir-Devops/AWS-ECS/assets/144611511/9f5d6ab8-00b5-4f0b-a508-bac955632457)

<hr/>

We are now ready to create our ECS fargate that runs Jenkins in a docker container,<br/>Fargate is the type of ECS cluster that will allow us to have serverless deployment, so we won't have to worry about provisioning for resources<br/>AWS will take care of that for us
as we run our applications.

Below is the screeshot of our cluster, when configuring:
 - Use ecsTask Role you have created
 - Choose Fargate Infrastructure

![image](https://github.com/Semir-Devops/AWS-ECS/assets/144611511/5f8dc57b-9683-457e-bd20-f77b0efe1374)

