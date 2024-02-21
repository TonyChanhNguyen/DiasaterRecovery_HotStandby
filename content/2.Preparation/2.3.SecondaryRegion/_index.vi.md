---
title : "Vùng thứ cấp"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 2.3 </b> "
---
### Triển khai cấu hình mạng sử dụng Amazon CloudFormation Templates
1. Tạo cấu hình hạ tầng mạng ở vùng thứ cấp **Oregon (us-west-2)** bằng việc khởi tạo [CloudFormation Template](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/template?stackName=network-stack&templateURL=https://ws-assets-prod-iad-r-pdx-f3b3f9f1a7d6a3d0.s3.us-west-2.amazonaws.com/6b7a41c6-3cae-45f2-bf2c-72c64b55d920/NetworkStack.yaml).
2. Tại trang CloudFormation, nhấn **Next**.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.1secondaryregion.png?width=90pc)


3. Tại trang **Specify stack details**, nhập tên stack ```network-stack```.
4. Sau đó, nhấn **Next**.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.2secondaryregion.png?width=90pc)

5. Tại trang **Configure stack options**. Cuộn xuống và nhấn **Next**.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.3secondaryregion.png?width=90pc)

6. Tại trang **Review network-stack**. Cuộn xuống và nhấn **Submit**.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.4secondaryregion.png?width=90pc)

7. Stack hạ tầng mạng đang được tạo.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.5secondaryregion.png?width=89pc)

8. Sau khoảng 1 phút, stack của bạn sẽ được tạo thành công.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.6secondaryregion.png?width=89pc)

### Triển khai ứng dụng
1. Tạo ứng dụng ở vùng thứ cấp **Oregon (us-west-2)** bằng việc khởi tạo [CloudFormation Template](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/template?stackName=hot-secondary&templateURL=https://ws-assets-prod-iad-r-pdx-f3b3f9f1a7d6a3d0.s3.us-west-2.amazonaws.com/6b7a41c6-3cae-45f2-bf2c-72c64b55d920/HotStandby.yaml).
2. Tại trang **Create stack**, nhấn **Next**.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.7secondaryregion.png?width=90pc)

3. Tại trang **Specify stack details**, nhập ```hot-secondary``` là **Stack name**.
4. Tại mục **Parameter**:
    + Thay đổi **no** ở **IsPrimary**.
    + Giữ **/aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2** ở **LatestAmiId** (mặc định).
    + Giữ **network-stack** ở **NetworkStackName** (mặc định), nếu bạn không thay đổi gì ở các bước trước đó.
5. Sau đó, nhấn **Next**.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.8secondaryregion.png?width=90pc)

6. Tại trang **Configure stack options**, cuộn xuống và nhấn **Next**.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.9secondaryregion.png?width=90pc)

7. Tại trang **Review hot-secondary**, cuộn xuống đến cuối trang. Sau đó, tích chọn ô **I acknowledge that AWS CloudFormation might create IAM resources with custom names.**
8. Nhấn **Next**.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.10secondaryregion.png?width=90pc)

9. Stack ứng dụng của bạn đang được tạo. Sẽ mất khoảng 15 phút để hoàn tất.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.11secondaryregion.png?width=90pc)

10. Sau khoảng 15 phút, stack của bạn sẽ được tạo thành công.
![Secondary Region](/images/2.preparation/2.3.secondaryregion/2.3.12secondaryregion.png?width=90pc)