---
title : "Kiểm tra chế độ dự phòng"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---

Amazon S3 bucket lưu trữ trang web Hot-Primary hiện không thể truy cập được. Khi CloudFront cố gắng định tuyến yêu cầu của người dùng đến khu vực chính, nó sẽ nhận được lỗi trạng thái HTTP 403 (Forbidden) giống như bạn đã làm. Phân phối CloudFront sẽ tự động xử lý tình huống này bằng cách chuyển dự phòng sang khu vực Hot-Secondary.

Nếu bạn quay lại và làm mới trình duyệt của mình (sử dụng CloudFront Distribution’s Domain Name trước đó), bạn sẽ thấy trang web **The Unicorn Shop - us-west-2**. Phiên của người dùng vẫn đang hoạt động và giỏ hàng của họ vẫn chứa các sản phẩm đã thêm trước đó.

1. Đi đến [CloudFront Distributions](https://us-east-1.console.aws.amazon.com/cloudfront/v4/home?region=ap-southeast-1#/distributions).
2. Sao chép **Domain name** vào trình duyệt web.
![Failover](/images/5.verifyfailover/5.1verifyfailover.png?width=90pc)

3. Xác nhận rằng tiêu đề của website thể hiện **The Unicorn Shop - us-west-2** và số lượng của **Cart Shop** giống với trước đó sau khi bạn đã đăng nhập thành công.
![Failover](/images/5.verifyfailover/5.2verifyfailover.png?width=90pc)


#### Chúc mừng, website của bạn đã được chuyển đổi dự phòng sang vùng thứ cấp **Oregon (us-west-2)** từ vùng chính **N. Virginia (us-east-1)** thành công.