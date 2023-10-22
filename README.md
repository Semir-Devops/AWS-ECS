# AWS-ECS

AWS ECS (Elastic Container service) is used to run docker containers from a fully managed service<br/>without having to worry about provisioning of compute resources.<br/>



In this project I am creating an ECS cluster to run a Jenkins application, a docker image pulled from Dockerhub,<br/>& exposing it through an ALB to allow access to it.

<hr/>

## Prerequisites:

 - ALB (with port 80 listener)
 - Jenkins Docker image found <a href="https://hub.docker.com/r/jenkins/jenkins">here</a>
