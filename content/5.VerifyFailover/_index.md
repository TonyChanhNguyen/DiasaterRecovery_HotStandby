---
title : "Verify failover"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---
Your Amazon S3 bucket that hosts the Hot-Primary website is now inaccessible. When CloudFront attempts to route the user’s request to the primary region, it will receive an HTTP 403 status error (Forbidden) just like you did. The CloudFront Distribution will automatically handle this scenario by failing over to the Hot-Secondary region.

If you go back and refresh your browser (using the CloudFront Distribution’s Domain Name from before), you should now see **The Unicorn Shop - us-west-2** website. The user’s session should still be active, and their cart still contains the products previously added.

1. Go to [CloudFront Distributions](https://us-east-1.console.aws.amazon.com/cloudfront/v4/home?region=ap-southeast-1#/distributions).
2. Copy the **Domain name** into a new browser window.
![Failover](/images/5.verifyfailover/5.1verifyfailover.png?width=90pc)

3. Confirm that the website's header says **The Unicorn Shop - us-west-2** and quantity of **Cart Shop** same as before after you log in successfully.
![Failover](/images/5.verifyfailover/5.2verifyfailover.png?width=90pc)


#### Congratulations, your website had been done failover to Secondary Region **Oregon (us-west-2)** from Primary Region **N. Virginia (us-east-1)** successfully.