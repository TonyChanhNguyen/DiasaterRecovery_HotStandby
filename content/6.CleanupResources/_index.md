---
title : "Cleanup resources"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

### S3 Cleanup
1. Go to [S3](https://s3.console.aws.amazon.com/s3/home).
2. Select the **hot-primary-uibucket-xxxx**.
3. Click **Empty**.
![Cleanup Resources](../images/6.cleanup/6.1cleanup.png?width=90pc)

4. Input ```permanently delete```.
5. Then, click on **Empty**.
![Cleanup Resources](../images/6.cleanup/6.2cleanup.png?width=90pc)

6. Repeat those steps for buckets:
    + **hot-primary-assetbucket-xxxx**.
    + **hot-secondary-uibucket-xxxx**.
    + **hot-secondary-assetbucket-xxxx**.

### Amazon DynamoDB Cleanup
1. Go to [Amazon DynamoDB](https://us-east-1.console.aws.amazon.com/dynamodb/home?region=us-east-1#/) at region **N. Virginia (us-east-1)**.
2. Click on **Tables** tab.
3. Click on **unishophotstandby** table.
![Cleanup Resources](../images/6.cleanup/6.3cleanup.png?width=90pc)

4. Click the **Global Tables** tab.
![Cleanup Resources](../images/6.cleanup/6.4cleanup.png?width=90pc)

5. Select **US West (Oregon)** replica.
6. Click on **Delete replica**.
![Cleanup Resources](../images/6.cleanup/6.5cleanup.png?width=90pc)

7. Input ```delete``` to confirm.
8. Then, click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.6cleanup.png?width=90pc)


### CloudFront Cleanup
1. Go to [CloudFront Distributions](https://us-east-1.console.aws.amazon.com/cloudfront/v4/home?region=us-east-1#/distributions).
2. Select distributions had created.
3. Click on **Disable**.
![Cleanup Resources](../images/6.cleanup/6.7cleanup.png?width=90pc)

4. Click on **Disable**.
![Cleanup Resources](../images/6.cleanup/6.8cleanup.png?width=90pc)

5. Wait for **Status** to be **Disabled** and for **Last Modified** to have a date.
![Cleanup Resources](../images/6.cleanup/6.9cleanup.png?width=90pc)

6. Then, select it again.
7. Click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.10cleanup.png?width=90pc)

8. Click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.11cleanup.png?width=90pc)


### Database Cleanup
#### Secondary region
1. Go to [RDS](https://us-west-2.console.aws.amazon.com/rds/home?region=us-west-2#databases:) in **Oregon (us-west-2)** region.
2. Select **unishop-hot** database under **hot-secondary** cluster.
3. Click on **Action**.
4. Then click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.12cleanup.png?width=90pc)

5. Enter ```delete me```.
6. Click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.13cleanup.png?width=90pc)

7. After **unishop-hot** database was deleted, select **hot-secondary** cluster.
8. Click on **Actions**.
9. Click on **Remove from global database**.
![Cleanup Resources](../images/6.cleanup/6.14cleanup.png?width=90pc)

10. Click **Remove and promote**.
![Cleanup Resources](../images/6.cleanup/6.15cleanup.png?width=90pc)


11. After remove from global database, select **hot-secondary** cluster.
12. Click on **Actions**.
13. Click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.16cleanup.png?width=90pc)

14. Uncheck **Create final snapshot** box.
15. Check **I acknowledge that upon instance...** box.
16. Input ```delete me```.
17. Then, click on **Delete DB sluster**.
![Cleanup Resources](../images/6.cleanup/6.17cleanup.png?width=90pc)

#### Primary region
1. Go to [RDS](https://us-east-1.console.aws.amazon.com/rds/home?region=us-east-1#databases:) in **N. Virginia (us-east-1)** region.
2. Repeat all above steps to delete **unishop-hot** database first, then delete **hot-primary** cluster.

After databases and clusters were deleted, now we will delete **Global database**.

3. Select **hot-global**.
4. Click on **Actions**.
5. Click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.18cleanup.png?width=90pc)

6. Input ```delete me```.
7. Click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.19cleanup.png?width=90pc)


### CloudFormation Secondary Region Cleanup
1. Go to [CloudFormation stacks](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/outputs?filteringText=&filteringStatus=active&viewNested=true) in the **Oregon (us-west-2)** region.
2. Select stack name **hot-secondary**.
3. Then click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.20cleanup.png?width=90pc)

4. Click on **Delete** to confirm. 
![Cleanup Resources](../images/6.cleanup/6.21cleanup.png?width=90pc)

5. After stack **hot-secondary** was deleted, select stack name **network-stack**.
6. Then click on **Delete**.
![Cleanup Resources](../images/6.cleanup/6.22cleanup.png?width=90pc)

7. Click on **Delete** to confirm.
![Cleanup Resources](../images/6.cleanup/6.23cleanup.png?width=90pc)

### CloudFormation Primary Region Cleanup
1. Go to [CloudFormation stacks](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks?filteringText=&filteringStatus=active&viewNested=true) in the **N. Virginia (us-east-1)** region.

2. Repeat these steps to delete stack name **hot-primary** first, then delete stack name **network-stack**.

#### Congratulations, you had finished this workshop! 