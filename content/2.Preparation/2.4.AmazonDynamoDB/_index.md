---
title : "Amazon DynamoDB "
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 2.4 </b> "
---

When you create a DynamoDB global table , it consists of multiple replica tables (one per AWS Region) that DynamoDB treats as a single unit. Every replica has the same table name and the same primary key schema. When an application writes data to a replica table in one AWS region, DynamoDB propagates the write to the other replica tables in the other AWS regions automatically.

1. Click [DynamoDB Tables](https://us-east-1.console.aws.amazon.com/dynamodbv2/home?region=us-east-1#tables) to navigate to the dashboard in the **N. Virginia (us-east-1)** regions.
2. Click on **unishophotstandby** table.
![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.1amazondynamodb.png?width=90pc)

3. Click on **Global Tables** tab.
4. Click on **Create replica** button.
![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.2amazondynamodb.png?width=90pc)

5. Select **US West (Oregon)** at **Available replication Regions**.
6. Then, click on **Create replica**. 
![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.3amazondynamodb.png?width=90pc)

7. Your replica is creating.
![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.4amazondynamodb.png?width=90pc)

{{%notice warning%}}
Wait for the status to show Active before moving on to the next step.
{{%/notice%}}

![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.5amazondynamodb.png?width=90pc)