---
title : "Kiểm tra website"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 2.5 </b> "
---

### Vùng chính
1. Nhấn [CloudFormation Stacks](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/stackinfo?filteringText=&filteringStatus=active&viewNested=true) để chuyển hướng đến trang chủ tại khu vực **N. Virginia (us-east-1)**.
2. Chọn stack **hot-primary**.
3. Nhấn vào đường dẫn **Output**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.1verifywebsite.png?width=90pc)

4. Nhấn vào đường dẫn **WebsiteURL** và mở nó trong trình duyệt web.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.2verifywebsite.png?width=90pc)

5. Tại trang web, nhấn **Sign up** để tạo tài khoản.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.3verifywebsite.png?width=89pc)

6. Nhập các thông tin cần thiết để tạo tài khoản.
7. Sau dó, nhấn **Signup** để hoàn tất bước này.

{{%notice warning%}}
Lưu trữ các thông tin này lại để cung cấp cho các bước tiếp theo.
{{%/notice%}}
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.4verifywebsite.png?width=90pc)

8. Nhấn **Log in**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.5verifywebsite.png?width=89pc)
9. Nhập các thông tin mà bạn đã điền.
10. Sau đó, nhấn **Login**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.6verifywebsite.png?width=90pc)

11. Sau khi đăng nhập thành công, nhấn vào sản phẩm **Unicorn** bạn muốn. Sau đó nhấn **Add to cart** để thêm vào giỏ hàng của bạn.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.7verifywebsite.png?width=90pc)

12. Sau khi thêm sản phẩm **Unicorn** vào giỏ hàng thành công, kiểm tra biểu tượng **Cart** để thấy số lượng đã được tăng lên.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.8verifywebsite.png?width=90pc)

13. Lặp lại bước 12 để thêm nhiều sản phẩm hơn vào giỏ hàng.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.9verifywebsite.png?width=90pc)

14. Sau khi hoàn tất các bước trên. Lưu lại số lượng của giỏ hàng và khu vực của nó. Chúng ta sẽ kiểm tra chúng lại sau khi thực hiện nhân bản ứng dụng web đến vùng thứ cấp.

{{%notice note%}}
Trong trường hợp này, số lượng ở giỏ hàng là **8** và khu vực là **us-east-1** (Vùng chính).
{{%/notice%}}
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.10verifywebsite.png?width=90pc)


### Vùng thứ cấp
Bạn đang tận dụng ưu điểm của bảng chung Amazon DynamoDB. Một bảng chung là tập hợp của một hoặc nhiều bảng sao, tất cả được sở hữu bởi một tài khoản AWS. Một bảng sao là một bảng DynamoDB duy nhất có chức năng như một phần của bảng chung. Mỗi bản sao lưu trữ tập dữ liệu giống nhau.

1. Đi đến [CloudFormation Stacks](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/outputs?filteringText=&filteringStatus=active&viewNested=true) ở khu vực **Oregon (us-west-2)**.
2. Chọn stack **hot-secondary**.
3. Nhấn vào thành chuyển hướng **Outputs**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.11verifywebsite.png?width=90pc)

4. Nhấn vào đường dẫn **WebsiteURL** và mở nó trong trình duyệt web.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.12verifywebsite.png?width=90pc)

5. Tại trang web bạn có thể thấy hiện giờ khu vực là **us-west-2**, sau đó nhấn **Log in**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.13verifywebsite.png?width=90pc)

6. Điền tất cả thông tin đã tạo ở vùng chính **N. Virginia (us-east-1)**.
7. Nhấn **Log in**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.14verifywebsite.png?width=90pc)

8. Bạn sẽ thấy số lượng ở giỏ hàng sẽ giống với số lượng mà bạn đã thêm ở vùng chính **N. Virginia (us-east-1)**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.15verifywebsite.png?width=90pc)

9. Hãy thêm sản phẩm vào giỏ hàng. 
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.16verifywebsite.png?width=90pc)

{{%notice note%}}
Tại thời điểm này, số lượng trong giỏ hàng là **10** và khu vực là **us-west-2** (Vùng thứ cấp).
{{%/notice%}}

10. Trở lại trang web của vùng chính **N. Virginia (us-east-1)** và kiểm tra giỏ hàng. Số lượng ở giỏ hàng hiện tại là **10**, giống tại vùng thứ cấp **Oregon (us-west-2)**.
![Verify website](/images/2.preparation/2.5.verifywebsite/2.5.17verifywebsite.png?width=90pc)
