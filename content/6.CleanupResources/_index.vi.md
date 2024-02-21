---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 6 
chapter : false
pre : " <b> 6. </b> "
---

### Dọn dẹp S3
1. Đi đến [S3](https://s3.console.aws.amazon.com/s3/home).
2. Chọn bucket **hot-primary-uibucket-xxxx**.
3. Nhấn **Empty**.
![Cleanup Resources](../../images/6.cleanup/6.1cleanup.png?width=90pc)

4. Nhập ```permanently delete```.
5. Sau đó, nhấn **Empty**.
![Cleanup Resources](../../images/6.cleanup/6.2cleanup.png?width=90pc)

6. Lặp lại các bước trên với bucket:
    + **hot-primary-assetbucket-xxxx**.
    + **hot-secondary-uibucket-xxxx**.
    + **hot-secondary-assetbucket-xxxx**.

### Dọn dẹp Amazon DynamoDB
1. Đi đến [Amazon DynamoDB](https://us-east-1.console.aws.amazon.com/dynamodb/home?region=us-east-1#/) tại khu vực **N. Virginia (us-east-1)**.
2. Nhấn thanh điều hướng **Tables**.
3. Chọn bảng **unishophotstandby**.
![Cleanup Resources](../../images/6.cleanup/6.3cleanup.png?width=90pc)

4. Nhấn thanh điều hướng **Global Tables**.
![Cleanup Resources](../../images/6.cleanup/6.4cleanup.png?width=90pc)

5. Chọn bản sao **US West (Oregon)**.
6. Nhấn **Delete replica**.
![Cleanup Resources](../../images/6.cleanup/6.5cleanup.png?width=90pc)

7. Nhập ```delete``` để xác nhận.
8. Sau đó, nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.6cleanup.png?width=90pc)


### Dọn dẹp CloudFront
1. Đi đến [CloudFront Distributions](https://us-east-1.console.aws.amazon.com/cloudfront/v4/home?region=us-east-1#/distributions).
2. Chọn Distributions vừa tạo.
3. Nhấn **Disable**.
![Cleanup Resources](../../images/6.cleanup/6.7cleanup.png?width=90pc)

4. Nhấn **Disable**.
![Cleanup Resources](../../images/6.cleanup/6.8cleanup.png?width=90pc)

5. Chờ đến khi **Status** chuyển sang **Disabled** và **Last Modified** có ngày.
![Cleanup Resources](../../images/6.cleanup/6.9cleanup.png?width=90pc)

6. Sau đó, chọn lại Distributions.
7. Nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.10cleanup.png?width=90pc)

8. Nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.11cleanup.png?width=90pc)


### Dọn dẹp CSDL
#### Vùng thứ cấp
1. Đi đến [RDS](https://us-west-2.console.aws.amazon.com/rds/home?region=us-west-2#databases:) ở khu vực **Oregon (us-west-2)**.
2. Chọn CSDL **unishop-hot** dưới cụm **hot-secondary**.
3. Nhấn **Action**.
4. Sau đó nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.12cleanup.png?width=90pc)

5. Nhập ```delete me```.
6. Sau đó nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.13cleanup.png?width=90pc)

7. Sau khi CSDL **unishop-hot** đã được xóa, chọn cụm **hot-secondary**.
8. Nhấn **Actions**.
9. Nhấn **Remove from global database**.
![Cleanup Resources](../../images/6.cleanup/6.14cleanup.png?width=90pc)

10. Nhấn **Remove and promote**.
![Cleanup Resources](../../images/6.cleanup/6.15cleanup.png?width=90pc)


11. Sau khi xóa khỏi global database, chọn cụm **hot-secondary**.
12. Nhấn **Actions**.
13. Nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.16cleanup.png?width=90pc)

14. Bỏ chọn **Create final snapshot**.
15. Chọn **I acknowledge that upon instance...**
16. Nhập ```delete me```.
17. Sau đó, nhấn **Delete DB sluster**.
![Cleanup Resources](../../images/6.cleanup/6.17cleanup.png?width=90pc)

#### Vùng chính
1. Đi đến [RDS](https://us-east-1.console.aws.amazon.com/rds/home?region=us-east-1#databases:) ở khu vực **N. Virginia (us-east-1)**.
2. Lặp lại các bước trên để xóa CSDL **unishop-hot** trước tiên, sau đó xóa cụm **hot-primary**.

Sau khi CSDL và cụm đã được xóa, bây giờ chúng ta sẽ xóa **Global database**.

3. Chọn **hot-global**.
4. Nhấn **Actions**.
5. Nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.18cleanup.png?width=90pc)

6. Nhập ```delete me```.
7. Nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.19cleanup.png?width=90pc)


### Dọn dẹp CloudFormation vùng thứ cấp
1. Đi đến [CloudFormation stacks](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/outputs?filteringText=&filteringStatus=active&viewNested=true) ở khu vực **Oregon (us-west-2)**.
2. Chọn stack tên **hot-secondary**.
3. Sau đó nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.20cleanup.png?width=90pc)

4. Nhấn **Delete** để xác nhận. 
![Cleanup Resources](../../images/6.cleanup/6.21cleanup.png?width=90pc)

5. Sau khi stack **hot-secondary** đã được xóa, chọn stack tên **network-stack**.
6. Sau đó nhấn **Delete**.
![Cleanup Resources](../../images/6.cleanup/6.22cleanup.png?width=90pc)

7. Nhấn **Delete** để xác nhận.
![Cleanup Resources](../../images/6.cleanup/6.23cleanup.png?width=90pc)

### Dọn dẹp CloudFormation vùng chính
1. Đi đến [CloudFormation stacks](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks?filteringText=&filteringStatus=active&viewNested=true) khu vực **N. Virginia (us-east-1)**.

2. Lặp lại các bước trên để xóa stack tên **hot-primary** trước tiên, sau đó xóa stack tên **network-stack**.

#### Chúc mừng, bạn đã hoàn thành bài thực hành này! 