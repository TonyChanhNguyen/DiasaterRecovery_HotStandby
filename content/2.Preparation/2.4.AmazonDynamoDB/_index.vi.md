---
title : "Amazon DynamoDB"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 2.4 </b> "
---

Khi bạn tạo một DynamoDB global table, nó bao gồm nhiều bảng sao (một cho mỗi khu vực AWS) mà DynamoDB xử lý như một đơn vị duy nhất. Mỗi bảng sao có cùng tên bảng và khóa chính. Khi một ứng dụng ghi dữ liệu tới một bảng sao trong một khu vực AWS, DynamoDB tự động truyền lệnh ghi vào các bảng bản sao khác trong các khu vực AWS khác.

1. Nhấn [DynamoDB Tables](https://us-east-1.console.aws.amazon.com/dynamodbv2/home?region=us-east-1#tables) để chuyển hướng đến trang chủ trong khu vực **N. Virginia (us-east-1)**.
2. Nhấn bảng **unishophotstandby**.
![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.1amazondynamodb.png?width=90pc)

3. Nhấn thanh điều hướng **Global Tables**.
4. Nhấn nút **Create replica**.
![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.2amazondynamodb.png?width=90pc)

5. Chọn **US West (Oregon)** là **Available replication Regions**.
6. Sau đó, nhấn **Create replica**. 
![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.3amazondynamodb.png?width=90pc)

7. Bản sao đang được tạo.
![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.4amazondynamodb.png?width=90pc)

{{%notice warning%}}
Chờ cho đến khi trạng thái hiển thị là Active trước khi di chuyển qua bước tiếp theo.
{{%/notice%}}

![Amazon DynamoDB](/images/2.preparation/2.4.amazondynamodb/2.4.5amazondynamodb.png?width=90pc)