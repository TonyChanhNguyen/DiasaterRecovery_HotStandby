---
title : "CloudFront"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---
Bạn có thể cải thiện khả năng phục hồi và tăng tính khả dụng cho một vài trường hợp cụ thể bằng việc cài đặt CloudFront với tính năng chuyển đổi dự phòng ban đầu. 
### Tạo Amazon CloudFront Distribution
1. Đi đến [CloudFront](https://us-east-1.console.aws.amazon.com/cloudfront/v3/home#/).
2. Nhấn nút **Create a CloudFront Distribution**.
![CloudFront](/images/3.cloudfront/3.1cloudfront.png?width=90pc)

3. Chọn **hot-primary-uibucket-xxx** tại **Origin domain**.
4. Nhấn **Use website endpoint**.
![CloudFront](/images/3.cloudfront/3.2cloudfront.png?width=90pc)

5. Cuộn xuống tính năng **Cache key and origin requests**.
6. Chọn **CachingDisabled** ở **Cache policy**.
![CloudFront](/images/3.cloudfront/3.3cloudfront.png?width=90pc)

{{%notice info%}}
Một trong những mục đích của việc sử dụng CloudFront là làm giảm lượng truy cập mà máy chủ gốc của bạn phải phản hồi trực tiếp. Với bộ đệm CloudFront, nhiều đối tượng hơn được phục vụ từ các vị trí biên của CloudFront, gần người dùng của bạn hơn. Điều này làm giảm tải trên máy chủ gốc của bạn và giảm độ trễ. Tuy nhiên, hành vi đó che giấu cơ chế của bạn (vô hiệu hóa nhóm giao diện người dùng) khỏi việc mô phỏng chính xác tình trạng ngừng hoạt động.
{{%/notice%}} 

7. Tại mục **Web Application Firewall (WAF)**, chọn **Do not enable security protections**.
![CloudFront](/images/3.cloudfront/3.4cloudfront.png?width=90pc)

{{%notice info%}}
Cách tốt nhất để giữ an toàn cho ứng dụng của bạn khỏi các mối đe dọa web và lỗ hổng bảo mật phổ biến nhất bằng AWS WAF là chọn kích hoạt bảo vệ bảo mật. Các yêu cầu bị chặn sẽ bị dừng trước khi chúng đến được máy chủ web của bạn
{{%/notice%}}

8. Cuộn xuống cuối trang và nhấn nút **Create distribution**.
![CloudFront](/images/3.cloudfront/3.5cloudfront.png?width=90pc)

### Cấu hình Additional Origin
Bây giờ bạn sẽ thêm một Origin bổ sung và sử dụng **hot-secondary-uibucket-xxxx**.
1. Nhấn thanh điều hướng **Origins**.
2. Nhấn nút **Create origin**.
![CloudFront](/images/3.cloudfront/3.6cloudfront.png?width=90pc)

3. Chọn **hot-secondary-uibucket-xxx** tại **Origin domain**.
4. Nhấn nút **Use website endpoint**.
![CloudFront](/images/3.cloudfront/3.7cloudfront.png?width=90pc)

5. Cuộn xuống cuối trang và nhấn nút **Create origin**.
![CloudFront](/images/3.cloudfront/3.8cloudfront.png?width=90pc)

### Cấu hình Origin Group
1. Nhấn nút **Create Origin Group**.
![CloudFront](/images/3.cloudfront/3.9cloudfront.png?width=90pc)

2. Tại mục **Origins**, chọn **hot-primary-uibucket-xxxx** và nhấn **Add**.
![CloudFront](/images/3.cloudfront/3.10cloudfront.png?width=90pc)

3. Lặp lại các bước trên với **hot-secondary-uibucket-xxxx**. 
![CloudFront](/images/3.cloudfront/3.11cloudfront.png?width=90pc)

4. Nhập ```hot-standby-origin-group``` là **Name**
5. Tích chọn tất cả các ô chọn của tính năng **Failover criteria**.
6. Sau đó, nhấn **Create origin group**.
![CloudFront](/images/3.cloudfront/3.12cloudfront.png?width=90pc)

### Cấu hình Behaviors
1. Nhấn thanh điều hướng **Behaviors**.
2. Chọn **Default (*)**.
3. Sau đó, nhấn nút **Edit**.
![CloudFront](/images/3.cloudfront/3.13cloudfront.png?width=90pc)

4. Chọn **hot-standby-origin-group** là **Origin and Origin Groups**.
![CloudFront](/images/3.cloudfront/3.14cloudfront.png?width=90pc)

5. Cuộn xuống cuối trang và nhấn nút **Save changes**.
![CloudFront](/images/3.cloudfront/3.15cloudfront.png?width=90pc)

6. Nhấn đường dẫn **Distributions**.
![CloudFront](/images/3.cloudfront/3.16cloudfront.png?width=90pc)

7. Chờ đến khi **Status** chuyển thành **Enabled** và **Last Modified** có ngày.
![CloudFront](/images/3.cloudfront/3.17cloudfront.png?width=90pc)

### Kiểm tra Distribution
1. Sao chép **CloudFront Distribution's Domain Name** đến trình duyệt web.
![CloudFront](/images/3.cloudfront/3.18cloudfront.png?width=90pc)

2. Xác nhận rằng tiêu đề của website thể hiện **The Unicorn Shop - us-east-1** và số lượng của **Cart Shop** giống với trước đó sau khi bạn đã đăng nhập thành công.
![CloudFront](/images/3.cloudfront/3.19cloudfront.png?width=90pc)

{{%notice info%}}
Một trong những mục đích của việc sử dụng CloudFront là để hổ trợ phương thức HTTPS, lưu trữ một trang web tĩnh trong S3 không hỗ trợ giao thức này. Bạn nên sử dụng các phương pháp hay nhất khi lưu trữ trang web tĩnh trên AWS sử dụng CloudFront.
{{%/notice%}}