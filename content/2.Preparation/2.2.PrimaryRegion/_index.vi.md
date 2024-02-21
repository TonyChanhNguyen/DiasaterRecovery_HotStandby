---
title : "Vùng chính"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

### Triển khai cấu hình mạng sử dụng Amazon CloudFormation Templates
1. Tạo cấu hình hạ tầng mạng ở vùng chính **N. Virginia (us-east-1)** bằng việc khởi tạo [CloudFormation Template](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/template?stackName=network-stack&templateURL=https://ws-assets-prod-iad-r-iad-ed304a55c2ca1aee.s3.us-east-1.amazonaws.com/6b7a41c6-3cae-45f2-bf2c-72c64b55d920/NetworkStack.yaml).
2. Tại trang CloudFormation, nhấn **Next**.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.1primaryregion.png?width=90pc)

3. Tại trang **Specify stack details**, nhập tên stack ```network-stack```.
4. Sau đó, nhấn **Next**.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.2primaryregion.png?width=90pc)

5. Tại trang **Configure stack options**. Cuộn xuống và nhấn **Next**.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.3primaryregion.png?width=90pc)


6. Tại trang **Review network-stack**. Cuộn xuống và nhấn **Submit**.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.4primaryregion.png?width=90pc)

7. Stack hạ tầng mạng đang được tạo.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.5primaryregion.png?width=90pc)

8. Sau khoảng 1 phút, stack của bạn sẽ được tạo thành công.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.6primaryregion.png?width=90pc)

### Triển khai ứng dụng
1. Tạo ứng dụng ở vùng chính **N. Virginia (us-east-1)** bằng việc khởi tạo [CloudFormation Template](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/template?stackName=hot-primary&templateURL=https://ws-assets-prod-iad-r-iad-ed304a55c2ca1aee.s3.us-east-1.amazonaws.com/6b7a41c6-3cae-45f2-bf2c-72c64b55d920/HotStandby.yaml).
2. Tại trang **Create stack**, nhấn **Next**.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.7primaryregion.png?width=90pc)

3. Tại trang **Specify stack details**, nhập ```hot-primary``` là **Stack name**.
4. Tại mục **Parameter**:
    + Giữ **yes** ở **IsPrimary** (mặc định).
    + Giữ **/aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2** ở **LatestAmiId** (mặc định).
    + Giữ **network-stack** ở **NetworkStackName** (mặc định), nếu bạn không thay đổi gì ở các bước trước đó.
5. Sau đó, nhấn **Next**.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.8primaryregion.png?width=90pc)

6. Tại trang **Configure stack options**, cuộn xuống và nhấn **Next**.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.9primaryregion.png?width=90pc)

7. Tại trang **Review hot-primary**, cuộn xuống đến cuối trang. Sau đó, tích chọn ô **I acknowledge that AWS CloudFormation might create IAM resources with custom names.**
8. Nhấn **Next**.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.10primaryregion.png?width=90pc)

9. Stack ứng dụng của bạn đang được tạo. Sẽ mất khoảng 15 phút để hoàn tất.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.11primaryregion.png?width=90pc)

10. Sau khoảng 15 phút, stack của bạn sẽ được tạo thành công.
![Primary Region](../../../images/2.preparation/2.2.primaryregion/2.2.12primaryregion.png?width=90pc)
