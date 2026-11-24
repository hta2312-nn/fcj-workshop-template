---
title: "Bảo mật và vận hành"
date: 2026-11-24
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

### Tổng quan
| Mục | Nội dung |
|---|---|
| Mục đích | Nắm hiện trạng bảo mật, giám sát hoạt động và chi phí, đồng thời lập kế hoạch cải tiến. |
| Dịch vụ AWS | CloudWatch, AWS Budgets, IAM |

### 5.6.1 Hiện trạng bảo mật
| Hạng mục | Hiện trạng | Rủi ro | Khuyến nghị |
|---|---|---|---|
| API Gateway | Đã giới hạn rate và burst trên stage v1 | Ai có URL đều gọi được và làm cạn quota Groq | Throttling, usage plan hoặc API key; Cognito sau này |
| CORS | Access-Control-Allow-Origin: * | Mọi website đều gọi được API từ trình duyệt | Giới hạn theo origin của trang S3 sau khi demo |
| Groq API key | Biến môi trường của Lambda | Lộ nếu bị commit hoặc chụp màn hình | Chuyển sang SSM Parameter Store (SecureString); đổi key nếu bị lộ |
| S3 website | Đọc công khai, chỉ HTTP | Lưu lượng không được mã hóa | Đặt CloudFront phía trước để có HTTPS nếu cần |
| Dữ liệu gửi tới Groq | Câu hỏi rời khỏi AWS | Dữ liệu khách hàng thật có thể ra ngoài tài khoản | Chỉ dùng câu hỏi mẫu; xem chính sách dữ liệu của Groq; cân nhắc Bedrock |
| CloudWatch | Đã bật log cho Lambda | Log có thể chứa câu hỏi của người dùng | Đặt thời gian lưu 7 đến 14 ngày; tránh log nội dung nhạy cảm |

### 5.6.2 Giám sát và kiểm soát chi phí
**Mục tiêu:** Phát hiện sớm lỗi và chi phí bất thường.

**Các bước**
1. Đặt thời gian lưu log cho log group của Lambda.
2. Tạo alarm cho lỗi của Lambda (tùy chọn).
3. Thường xuyên xem trang Free Tier usage trong Billing và giữ cảnh báo Budget đã thiết lập ở mục 5.2.

**Xem log trong CloudWatch**
1. Vào trang tổng quan CloudWatch, mở mục **Logs** để xem log của Lambda.

![Trang tổng quan CloudWatch, mục Logs](../../images/5-Workshop/5.6/5-6-01.png)

2. Trong danh sách **Log groups**, chọn log group của hàm Lambda do Lambda tự tạo.

![Danh sách Log groups](../../images/5-Workshop/5.6/5-6-02.png)

3. Trong danh sách **Log streams**, mỗi stream ghi lại các request của hàm kèm thời điểm log gần nhất.

![Danh sách Log streams](../../images/5-Workshop/5.6/5-6-03.png)

**Kiểm tra:** request thử nghiệm xuất hiện trong log, và cảnh báo Budget đang hoạt động.

### 5.6.3 Lộ trình siết bảo mật
1. Thêm throttling và usage plan cho API để bảo vệ quota Groq. Đây là ưu tiên cao và không cần sửa frontend.
2. Chuyển Groq key sang SSM Parameter Store, chỉ cấp cho Lambda quyền đọc đúng parameter đó.
3. Giới hạn CORS theo origin của website.
4. Thêm đăng nhập Cognito nếu hệ thống rời khỏi chế độ demo.
5. Kiểm thử: gọi API với tốc độ cao để xác nhận throttling, thử câu hỏi prompt injection, và quét repository để tìm secret.

**Đặt giới hạn throttling cho stage**
1. Trang Throttling của stage hiển thị các mức giới hạn đang áp dụng. Chọn stage cần giới hạn ở góc phải phía trên. Ảnh hiện đang ở stage $default. Mỗi stage có cấu hình throttling riêng.
   - **Selected route throttling:** giới hạn riêng cho từng route, ghi đè mức mặc định. Mục này đang trống vì chưa chọn route nào.
   - **Default route throttling:** giới hạn áp dụng cho mọi route trong stage. Hiện Burst limit và Rate limit đều ghi "Not configured", nghĩa là chưa giới hạn gì.
   - **Account throttling:** mức trần chung của cả tài khoản trong region (Burst 5000, Rate 10000), dùng chung cho mọi API. Đây là mức hệ thống, không chỉnh tại đây.

![Trang Throttling của stage](../../images/5-Workshop/5.6/5-6-04.png)

2. Chọn **Edit** ở mục Default route throttling và đặt:
   - **Rate limit:** 5, số request trung bình tối đa mỗi giây.
   - **Burst limit:** 2, số request tối đa được xử lý đồng thời trong một đợt tăng đột biến.
3. Chọn **Save**, sau đó chọn **Deploy** để áp dụng.

*[Hình: Đặt Burst limit = 2 và Rate limit = 5 cho route mặc định]*

Request vượt giới hạn sẽ nhận lỗi 429 Too Many Requests từ API Gateway, trước khi tới Lambda và Groq.
