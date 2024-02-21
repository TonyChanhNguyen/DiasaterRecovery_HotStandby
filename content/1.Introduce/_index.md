---
title : "Introduce"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
### Overview
In this module, you will go through the Hot Standby disaster recovery strategy. Hot Standby disaster recovery strategy has Recovery Point Objective(RPO) / Recovery Time Objective (RTO)  in almost real time. For the hot standby strategy secondary region, the data is live, core infrastructure is provisioned and the services are running at full production capacity.

Your application is currently deployed in the primary region N. Virginia (us-east-1). Oregon (us-west-2) will be your secondary region.

Your test application is Unishop. It is a Spring Boot Java application deployed on a single Amazon Elastic Compute Cloud (EC2)  instance using a public subnet. Your datastore is an Amazon Aurora  MySQL database which has user data. Your test application is also deployed using Amazon API Gateway  and AWS Lambda . Your datastore is Amazon DynamoDB  which has shopping cart data. The frontend is written using bootstrap and hosted in Amazon Simple Storage Service (S3) .

Your test application is using two datastores, Amazon Aurora and Amazon DynamoDB to showcase the Disaster Recovery features of each. You are using Amazon DynamoDB to store the state of the shopping cart and you are using Amazon Aurora to store the unicorn product catalog. When you initiate failover, for the Amazon Aurora database you will not need to promote the read replica in the recovery region since you are only reading the product catalog. This can decrease recovery time since no database promotion is necessary. In the failover case of Amazon DynamoDB you have configured Global Tables which allows for multiple writers so no action is needed. For your workloads, you would choose the right datastore for your use case.

This module takes advantage of Amazon CloudFront  which you will use as your content delivery network. You are also taking advantage of Amazon Aurora Global Database  to replicate your Amazon Aurora MySQL data to your secondary region and Amazon DynamoDB Global Tables  to replicate your DynamoDB data to your secondary region.

CloudFormation  will be used to configure the infrastructure and deploy the application. Provisioning your infrastructure with infrastructure as code (IaC) methodologies is a best practice. CloudFormation is an easy way to speed up cloud provisioning with infrastructure as code.

![Hot Standby](/images/hotstandby.png?width=60pc)

### Content

1. [Introduce](../1.introduce/)
2. [Preparation](../2.preparation/)
    - 2.1 [S3 access](../2.preparation/2.1.s3access/)
    - 2.2 [Primary region](../2.preparation/2.2.primaryregion/)
    - 2.3 [Secondary region](../2.preparation/2.3.secondaryregion/)
    - 2.4 [Amazon DynamoDB](../2.preparation/2.4.amazondynamodb/)
    - 2.5 [Verify website](../2.preparation/2.5.verifywebsite/)
3. [CloudFront](../3.cloudfront/)
4. [Failover](../4.failover/)
5. [Verify failover](../5.verifyfailover/)
6. [Cleanup resources](../6.cleanupresources/)

