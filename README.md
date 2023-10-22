# AWS-ECS

AWS ECS (Elastic Container service) is used to run docker containers from a fully managed service<br/>without having to worry about provisioning of compute resources.<br/>



In this project I am creating an ECS cluster to run a Jenkins application, a docker image pulled from Dockerhub,<br/>& exposing it through an ALB to allow access to it.

<hr/>

## Prerequisites:

 - ALB (with port 80 inbound listener open & target group listener on port 8080)
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

<hr/>

The next step is to create a Task definition, this will add the Jenkins docker image to your AWS to run it & allows to be reused in other clusters.

When configuring:
 - Use the docker image URI above in the container section with containr port mapped to 8080 using HTTP
 - Fargate Launch Type
 - ecsTask Role you have created

![image](https://github.com/Semir-Devops/AWS-ECS/assets/144611511/8ed8dfd3-0522-443c-97b6-c801a9fac31b)

<hr/>

Now that we have a task ready to be run, we will create a service under our new cluster

When configuring:
 - Use Task definition you have created
 - Fargate Launch Type
 - Service application type
 - Any security group with port 80 http inbound rule & TCP inbound rule allowing your ALB secutiry group
 - configure your Load Balancer you have created

The security Group:

![image](https://github.com/Semir-Devops/AWS-ECS/assets/144611511/d746cca5-b146-420b-8b84-fb8e83b1c96d)

The target group:

![image](https://github.com/Semir-Devops/AWS-ECS/assets/144611511/0a82bc37-6795-463e-8227-a342ba11c6e8)


If everything has been configured correctly, your final step is to access your container from the ALB DNS name.<br/>You should see the Jenkins setup page:

![image](https://github.com/Semir-Devops/AWS-ECS/assets/144611511/a1145858-8823-40e7-8204-cdb5aa0285e9)
