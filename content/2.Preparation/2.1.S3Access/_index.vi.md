---
title : "Truy cập S3"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---
Ứng dụng của bạn sử dụng AWS Simple Storage Service (S3) để lưu trữ website tĩnh. Để giúp ứng dụng khả dụng với người dùng Internet, bạn phải vô hiệu hóa chính sách tài khoản AWS đã chặn truy cập công khai.

1. Nhấn [S3](https://s3.console.aws.amazon.com/s3/home) to navigate to the dashboard.
2. Chọn chức năng **Block Public Access settings for this account**.

![S3 Access](../../../images/2.preparation/2.1.s3access/2.1.1s3access.png?width=90pc)

3. Nếu bạn thấy rằng **Block public access** là **On**, nhấn nút **Edit**.

{{%notice note%}}
Nếu bạn thấy rằng **Block public access** là **Off**, bạn có thể bỏ qua bước này và đi đến [Primary region](../2.preparation/2.2.primaryregion/).
{{%/notice%}}

![S3 Access](../../../images/2.preparation/2.1.s3access/2.1.2s3access.png?width=90pc)

4. Bỏ chọn **Block all public access**.
5. Sau đó, nhấn **save changes**.
![S3 Access](../../../images/2.preparation/2.1.s3access/2.1.3s3access.png?width=90pc)

6. Nhập ```confirm```, sau đó nhấn **Confirm** để lưu lại các thay đổi của bạn.
![S3 Access](../../../images/2.preparation/2.1.s3access/2.1.4s3access.png?width=90pc)

7. Thay đổi của bạn đã được cập nhật thành công.
![S3 Access](../../../images/2.preparation/2.1.s3access/2.1.5s3access.png?width=90pc)