---
title : "CloudFront"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---
You can improve resiliency and increase availability for specific scenarios by setting up CloudFront with origin failover.

### Create the Amazon CloudFront Distribution
1. Go to [CloudFront](https://us-east-1.console.aws.amazon.com/cloudfront/v3/home#/).
2. Click the **Create a CloudFront Distribution** button.
![CloudFront](../images/3.cloudfront/3.1cloudfront.png?width=90pc)

3. Select **hot-primary-uibucket-xxx** at **Origin domain**.
4. Click on **Use website endpoint**.
![CloudFront](../images/3.cloudfront/3.2cloudfront.png?width=90pc)

5. Scroll down to **Cache key and origin requests** feature.
6. Select **CachingDisabled** as **Cache policy**.
![CloudFront](../images/3.cloudfront/3.3cloudfront.png?width=90pc)

{{%notice info%}}
One of the purposes of using CloudFront is to reduce the number of requests that your origin server must respond to directly. With CloudFront caching, more objects are served from CloudFront edge locations, which are closer to your users. This reduces the load on your origin server and reduces latency. However, that behavior masks your mechanism (disabling the UI bucket) from properly simulating an outage.
{{%/notice%}}

7. At **Web Application Firewall (WAF)** section, select **Do not enable security protections**.
![CloudFront](../images/3.cloudfront/3.4cloudfront.png?width=90pc)

{{%notice info%}}
Best practice to keep your application secure from the most common web threats and security vulnerabilities using AWS WAF is to select Enable security protections. Blocked requests are stopped before they reach your web servers.
{{%/notice%}}

8. Scroll down to the end of page and click the **Create distribution** button.
![CloudFront](../images/3.cloudfront/3.5cloudfront.png?width=90pc)

### Configure an Additional Origin
You will now add an additional Origin and use your **hot-secondary-uibucket-xxxx**.
1. Click the **Origins** tab.
2. Click the **Create origin** button.
![CloudFront](../images/3.cloudfront/3.6cloudfront.png?width=90pc)

3. Select **hot-secondary-uibucket-xxx** at **Origin domain**.
4. Click the **Use website endpoint** button.
![CloudFront](../images/3.cloudfront/3.7cloudfront.png?width=90pc)

5. Scroll down to the end of page and click the **Create origin** button.
![CloudFront](../images/3.cloudfront/3.8cloudfront.png?width=90pc)

### Configure the Origin Group
1. Click on **Create Origin Group** button.
![CloudFront](../images/3.cloudfront/3.9cloudfront.png?width=90pc)

2. At **Origins** section, select **hot-primary-uibucket-xxxx** and then click on **Add**.
![CloudFront](../images/3.cloudfront/3.10cloudfront.png?width=90pc)

3. Repeat above step with **hot-secondary-uibucket-xxxx**. 
![CloudFront](../images/3.cloudfront/3.11cloudfront.png?width=90pc)

4. Input ```hot-standby-origin-group``` as **Name**
5. Enable all checkboxes of **Failover criteria** feature.
6. Then, click on **Create origin group**.
![CloudFront](../images/3.cloudfront/3.12cloudfront.png?width=90pc)

### Configure Behaviors
1. Click the **Behaviors** tab.
2. Select **Default (*)**.
3. Then, click the **Edit** button.
![CloudFront](../images/3.cloudfront/3.13cloudfront.png?width=90pc)

4. Select **hot-standby-origin-group** as the **Origin and Origin Groups**.
![CloudFront](../images/3.cloudfront/3.14cloudfront.png?width=90pc)

5. Scroll down to the end of page and click the **Save changes** button.
![CloudFront](../images/3.cloudfront/3.15cloudfront.png?width=90pc)

6. Click the **Distributions** link.
![CloudFront](../images/3.cloudfront/3.16cloudfront.png?width=90pc)

7. Wait for **Status** to be **Enabled** and for **Last Modified** to have a date.
![CloudFront](../images/3.cloudfront/3.17cloudfront.png?width=90pc)

### Verify the Distribution
1. Copy the **CloudFront Distribution's Domain Name** into a new browser window.
![CloudFront](../images/3.cloudfront/3.18cloudfront.png?width=90pc)

2. Confirm that the website's header says **The Unicorn Shop - us-east-1** and quantity of **Cart Shop** same as before after you log in successfully.
![CloudFront](../images/3.cloudfront/3.19cloudfront.png?width=90pc)

{{%notice info%}}
One of the purposes of using CloudFront is to support HTTPS, hosting a static website in S3 does not support this protocol. You should use best practices when hosting a static website on AWS which is to use CloudFront.
{{%/notice%}}
