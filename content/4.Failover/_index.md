---
title : "Failover"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

When a regional service event affects the Unishop application in the primary region N. Virginia (us-east-1), we want to fail over to the secondary region Oregon (us-west-2).

### Simulating a Regional Service Event

You will now simulate a regional service event affecting the Unishop website in N. Virginia (us-east-1). You are going to achieve this by blocking public access to the S3 bucket that is hosting the website making the Unishop website unavailable.

1. Go to [S3](https://s3.console.aws.amazon.com/s3/home).
2. Click on the bucket name **hot-primary-uibucket-xxxxxxxxxxxx**.
![Failover](../images/4.failover/4.1failover.png?width=90pc)

3. Click on **Permissions** tab.
![Failover](../images/4.failover/4.2failover.png?width=90pc)

4. In the **Block public access (bucket settings)** section, click on **Edit**.
![Failover](../images/4.failover/4.3failover.png?width=90pc)

5. Enable the **Block all public access** checkbox.
6. Then click the **Save changes** button.
![Failover](../images/4.failover/4.4failover.png?width=90pc)

7. Input ```confirm```.
8. Click on **Confirm** to save your changes.
![Failover](../images/4.failover/4.5failover.png?width=90pc)

9. Click on **Properties** tab.
![Failover](../images/4.failover/4.6failover.png?width=90pc)

10. Scroll down to the **Static website hosting** section. Click on the **Bucket website endpoint** link.
![Failover](../images/4.failover/4.7failover.png?width=90pc)

11. You should get a 403 Forbidden error.
![Failover](../images/4.failover/4.8failover.png?width=90pc)