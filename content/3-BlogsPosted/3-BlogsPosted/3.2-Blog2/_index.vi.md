---
title: "Blog 2"
date: 2026-11-24
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# AWS LEARNING CORNER: NHỮNG ĐIỀU NGƯỜI MỚI CẦN BIẾT ĐỂ KHÔNG BỊ SỐC VÌ HÓA ĐƠN CUỐI THÁNG

Một tình huống phổ biến với người mới dùng AWS là bật một tài nguyên thử nghiệm, quên tắt, rồi nhận hóa đơn bất ngờ vào cuối tháng. Kiểm soát chi phí không chỉ giúp bạn yên tâm khi thực hành mà còn là kỹ năng nền tảng khi quản lý hạ tầng cloud.

Dưới đây là các thiết lập và mẹo quan trọng để quản lý ngân sách hiệu quả ngay từ đầu.

### 1. Thiết lập AWS Budgets và Billing Alerts
Đây là bước đầu tiên bạn nên làm ngay sau khi tạo tài khoản AWS.

* **Cách hoạt động:** Đặt một ngưỡng ngân sách an toàn (ví dụ $5 hoặc $10). Khi chi phí thực tế hoặc dự báo vượt ngưỡng này, hệ thống tự động gửi email thông báo.
* **Lợi ích:** Các tài nguyên chạy ngầm trong thời gian dài sẽ được phát hiện sớm.

### 2. Sử dụng AWS Free Tier đúng cách
Free Tier cung cấp nhiều tài nguyên miễn phí, nhưng mỗi loại đều có điều kiện riêng:

* **Giới hạn thời gian:** Ví dụ, EC2 có 750 giờ mỗi tháng cho các instance t2.micro hoặc t3.micro (tùy Region). Nếu bạn chạy hai instance liên tục, thời gian sử dụng được tính gấp đôi và bạn có thể vượt hạn mức miễn phí rất nhanh.
* **Giới hạn dung lượng:** S3 và EBS có quy định riêng về dung lượng lưu trữ và số lượng request. Hãy đọc kỹ điều khoản dịch vụ trước khi tạo tài nguyên.

### 3. Dọn dẹp tài nguyên không dùng
Các tài nguyên nhàn rỗi hoặc tồn tại độc lập thường là nguồn chi phí ẩn:

* **Dừng hoặc xóa EC2 instance:** Tắt các máy chủ thử nghiệm khi không làm việc.
* **Lưu ý về Elastic IP:** Elastic IP chỉ miễn phí khi được gắn vào một EC2 instance đang chạy. Nếu bạn gỡ ra, hoặc gắn vào instance đang dừng, bạn vẫn bị tính phí duy trì.
* **EBS volume và snapshot không gắn kết:** Khi xóa EC2 instance, một số EBS volume hoặc snapshot tự động tạo có thể vẫn còn và tiếp tục tính phí lưu trữ.

### 4. Theo dõi chi tiết với AWS Cost Explorer

* **Công cụ trực quan:** AWS Cost Explorer cung cấp biểu đồ phân tích chi phí theo thời gian, theo dịch vụ hoặc theo Tag.
* **Kiểm tra định kỳ:** Xem báo cáo chi phí một đến hai lần mỗi tuần giúp bạn nhanh chóng phát hiện dịch vụ tiêu tốn ngân sách bất thường.

### Kết luận
Tối ưu và kiểm soát chi phí là phần không thể thiếu trong tư duy làm việc với Cloud Computing. Thiết lập một môi trường an toàn ngay từ đầu giúp bạn học tập và thử nghiệm dịch vụ AWS mà không lo về hóa đơn.

Bạn có mẹo kiểm soát chi phí nào khác, hoặc câu chuyện đáng nhớ nào về hóa đơn AWS không? Chia sẻ bên dưới phần bình luận nhé.

[Liên kết bài đăng trên AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/posts/2317495209015438/)
