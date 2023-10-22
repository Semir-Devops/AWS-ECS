# AWS-ECS

AWS ECS (Elastic Container service) is used to run docker containers from a fully managed service<br/>without having to worry about provisioning of compute resources.<br/>



In this project I am creating an ECS cluster to run a Jenkins application, a docker image pulled from Dockerhub,<br/>& exposing it through an ALB to allow access to it.

<hr/>

## Prerequisites:

 - ALB (with port 80 listener open)
 - Jenkins Docker image found <a href="https://hub.docker.com/r/jenkins/jenkins">here</a>
 - ecsTaskExecutionRole Role to allow ECS to run on your account (IAM Role as shown below with permission):

![image](https://github.com/Semir-Devops/AWS-ECS/assets/144611511/9f5d6ab8-00b5-4f0b-a508-bac955632457)

<hr/>

