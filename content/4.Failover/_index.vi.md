---
title : "Chế độ dự phòng"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

Khi sự kiện thảm hỏa gây ảnh hưởng đến ứng dụng Unishop tại vùng chính N. Virginia (us-east-1), chúng ta sẽ phục hồi đến vùng thứ cấp Oregon (us-west-2).

### Mô phỏng sự kiện thảm họa

Bạn sẽ mô phỏng sự kiện thảm họa ảnh hưởng đến website Unishop tại N. Virginia (us-east-1). Bạn sẽ đạt được điều này bằng việc chặn các truy cập công khai đến S3 bucket nơi đang lưu trữ website để làm cho website Unishop không khả dụng.

1. Đi đến [S3](https://s3.console.aws.amazon.com/s3/home).
2. Chọn bucket tên **hot-primary-uibucket-xxxxxxxxxxxx**.
![Failover](../../images/4.failover/4.1failover.png?width=90pc)

3. Nhấn thanh chuyển hướng **Permissions**.
![Failover](../../images/4.failover/4.2failover.png?width=90pc)

4. Tại mục **Block public access (bucket settings)**, nhấn **Edit**.
![Failover](../../images/4.failover/4.3failover.png?width=90pc)

5. Tích chọn ô **Block all public access**.
6. Sau đó nhấn nút **Save changes**.
![Failover](../../images/4.failover/4.4failover.png?width=90pc)

7. Nhập ```confirm```.
8. Nhấn **Confirm** để lưu thay đổi của bạn.
![Failover](../../images/4.failover/4.5failover.png?width=90pc)

9. Nhấn thanh chuyển hướng **Properties**.
![Failover](../../images/4.failover/4.6failover.png?width=90pc)

10. Cuộn xuống mục **Static website hosting**. Nhấn vào đường dẫn **Bucket website endpoint**.
![Failover](../../images/4.failover/4.7failover.png?width=90pc)

11. Bạn sẽ nhận được mã lỗi 403 Forbidden.
![Failover](../../images/4.failover/4.8failover.png?width=90pc)