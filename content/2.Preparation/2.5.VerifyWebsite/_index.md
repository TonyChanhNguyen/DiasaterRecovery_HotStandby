---
title : "Verify website"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---

### Primary Region
1. Click [CloudFormation Stacks](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/stackinfo?filteringText=&filteringStatus=active&viewNested=true) to navigate to the dashboard in **N. Virginia (us-east-1)** region.
2. Choose the **hot-primary** stack.
3. Click the **Output** link.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.1verifywebsite.png?width=90pc)

4. Click on the **WebsiteURL** output link and open in a new browser tab or window.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.2verifywebsite.png?width=90pc)

5. At web page, click on **Sign up** to register account.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.3verifywebsite.png?width=89pc)

6. Fill needed information to sign up account.
7. Then, click on **Signup** to finish this step.

{{%notice warning%}}
Keep remember information which you provided for this step.
{{%/notice%}}
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.4verifywebsite.png?width=90pc)

8. Click on **Log in**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.5verifywebsite.png?width=89pc)
9. Fill information which you provided.
10. Then, click on **Login**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.6verifywebsite.png?width=90pc)

11. After log in successfully, click to **Unicorn** item you want. Then click on **Add to cart** to add it into your cart.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.7verifywebsite.png?width=90pc)

12. After you add **Unicorn** item to cart successfully, check **Cart** icon to see the quantity was increased.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.8verifywebsite.png?width=90pc)

13. Repeat step 12 to add more items to your cart.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.9verifywebsite.png?width=90pc)

14. After finish those steps. Save the quantity of your cart and its region. We will verify them again after performing replicate website into secondary region.

{{%notice note%}}
In my situation, the quantity of cart is **8** and region is **us-east-1** (Primary region).
{{%/notice%}}
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.10verifywebsite.png?width=90pc)


### Secondary Region
You are taking advantage of Amazon DynamoDB global tables. A global table is a collection of one or more replica tables, all owned by a single AWS account. A replica table (or replica, for short) is a single DynamoDB table that functions as a part of a global table. Each replica stores the same set of data items.

1. Go to [CloudFormation Stacks](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/outputs?filteringText=&filteringStatus=active&viewNested=true) in region **Oregon (us-west-2)**.
2. Choose the **hot-secondary** stack.
3. Click the **Outputs** link.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.11verifywebsite.png?width=90pc)

4. Click on the **WebsiteURL** output link and open in a new browser tab or window.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.12verifywebsite.png?width=90pc)

5. At web page you can see the region now is **us-west-2**, then click on **Log in**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.13verifywebsite.png?width=90pc)

6. Fill need information that you created at Primary region **N. Virginia (us-east-1)**.
7. Click on **Log in**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.14verifywebsite.png?width=90pc)

8. You should see the same number of items in your cart that you added at Primary region **N. Virginia (us-east-1)**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.15verifywebsite.png?width=90pc)

9. Lets add more items to the cart. 
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.16verifywebsite.png?width=90pc)

{{%notice note%}}
At this time, the quantity of cart is **10** and region is **us-west-2** (Secondary region).
{{%/notice%}}

10. Back to web page of Primary region **N. Virginia (us-east-1)** and see the cart. The quantity of cart now is **10**, same as at Secondary region **Oregon (us-west-2)**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.17verifywebsite.png?width=90pc)
