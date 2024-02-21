---
title : "S3 access "
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

Your application employs AWS Simple Storage Service (S3) Static website hosting. To make the application available to Internet users, you must disable the AWS account policy that blocks public access.

1. Click [S3](https://s3.console.aws.amazon.com/s3/home) to navigate to the dashboard.
2. Select feature **Block Public Access settings for this account**.

![S3 Access](../../images/2.preparation/2.1.s3access/2.1.1s3access.png?width=90pc)

3. If you see that **Block public access** is **On**, click on **Edit** button.

{{%notice note%}}
If you see that **Block public access** is **Off**, you can skip this step and to go [Primary region](../2.preparation/2.2.primaryregion/).
{{%/notice%}}

![S3 Access](../../images/2.preparation/2.1.s3access/2.1.2s3access.png?width=90pc)

4. Uncheck **Block all public access**.
5. Then, click on **save changes**.
![S3 Access](../../images/2.preparation/2.1.s3access/2.1.3s3access.png?width=90pc)

6. Input ```confirm```, then click on **Confirm** to save your changes.
![S3 Access](../../images/2.preparation/2.1.s3access/2.1.4s3access.png?width=90pc)

7. Your changes had been updated successfully.
![S3 Access](../../images/2.preparation/2.1.s3access/2.1.5s3access.png?width=90pc)