---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
### Giới thiệu
Trong bài thực hành này, bạn sẽ trải qua chiến lược khắc phục thảm họa Hot Standby. Chiến lược khắc phục thảm họa Hot Standby có thời điểm khắc phục  /  Thời gian phục hồi (**Recovery Point Objective(RPO) / Recovery Time Objective (RTO)**) thời gian thực. Đối với khu vực thứ cấp của chiến lược Hot Standby, dữ liệu sẽ hoạt động và cơ sở hạ tầng cốt lõi sẽ được cung cấp và các dịch vụ chạy với công suất tối đa.

Các ứng dụng hiện đang được triển khai tại khu vực chính N. Virginia (us-east-1). Oregon (us-west-2) sẽ là khu vực thứ cấp của bạn.

Ứng dụng mẫu của bạn là **Unishop**. Nó là một ứng dụng Spring Boot Java được triển khai trên một máy chủ Amazon Elastic Compute Cloud (EC2) sử dụng một mạng con công cộng. Vùng chứa dữ liệu của bạn là một CSDL Amazon Aurora  MySQL dùng để chứa dữ liệu của người dùng. Ứng dụng mẫu của bạn cũng được triển khai sử dụng API Gateway và AWS Lambda. Vùng chứa dữ liệu của bạn là Amazon DynamoDB dùng chứa dữ liệu của giỏ hàng mua sắm. Giao diện người dùng được viết bằng bootstrap và được lưu trữ trên Amazon Simple Storage Service (S3).

Ứng dụng mẫu này có hai vùng chứa dữ liệu, Amazon Aurora và Amazon DynamoDB giới thiệu tính năng phục hồi sau thảm họa của mỗi vùng chứa dữ liệu. Bạn sẽ sử dụng Amazon DynamoDB để chứa trạng thái giỏ hàng mua sắm và Amazon Aurora để lưu trữ danh mục sản phẩm Unicorn. Khi bạn bắt đầu chuyển đổi dự phòng, đối với CSDL Amazon Aurora bạn sẽ không cần phải thực hiện nâng cấp trong khu vực phục hồi vì bạn chỉ cần đọc danh mục sản phẩm. Điều này có thể làm giảm thời gian phục hồi vì không cần thiết nâng cấp CSDL nào. Trong trường hợp chuyển đổi dự phòng Amazon DynamoDB bạn cấu hình Global Tables mà cho phép bạn ghi đồng thời vì thế không cần thêm bất kì thao tác nào. Đối với khối lượng công việc của bạn, bạn sẽ chọn vùng chứa dữ liệu phù hợp cho trường hợp sử dụng của mình.

Bài thực hành này tận dụng ưu điểm của Amazon CloudFront mà bạn sẽ sử dụng như là mạng lưới phân phối nội dung của bạn. Bạn cũng sẽ tận dụng ưu điểm của Amazon Aurora Global Database để nhân bản dữ liệu Amazon Aurora MySQL của bạn đến vùng thứ cấp và Amazon DynamoDB Global Tables để nhân bản dữ liệu DynamoDB đến vùng thứ cấp của bạn.

CloudFormation sẽ được sử dụng để cấu hình cơ sở hạ tầng và triển khai ứng dụng. Cung cấp cơ sở hạ tầng của bạn với các phương thức cơ sở hạ tầng bằng code (IaC) là phương pháp tổt nhất. CloudFormation là một cách đơn giản để tăng tốc việc cung cấp dịch vụ đám mây với cơ sở hạ tầng bằng code.

![Hot Standby](/images/hotstandby.png?width=60pc)


### Nội dung

1. [Giới thiệu](../1.introduce/)
2. [Các bước chuẩn bị](../2.preparation/)
    - 2.1 [Truy cập S3](../2.preparation/2.1.s3access/)
    - 2.2 [Vùng chính](../2.preparation/2.2.primaryregion/)
    - 2.3 [Vùng thứ cấp](../2.preparation/2.3.secondaryregion/)
    - 2.4 [Amazon DynamoDB](../2.preparation/2.4.amazondynamodb/)
    - 2.5 [Kiểm tra website](../2.preparation/2.5.verifywebsite/)
3. [CloudFront](../3.cloudfront/)
4. [Chuyển đổi dự phòng](../4.failover/)
5. [Kiểm tra chuyển đổi dự phòng](../5.failover/)
6. [Dọn dẹp tài nguyên](../6.cleanupresources/)

