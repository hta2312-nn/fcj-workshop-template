---
title: "5.2 Chuẩn bị"
date: 2026-11-24
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

### Tài khoản AWS và region
Toàn bộ tài nguyên được tạo trong một region: **ap-southeast-2 (Asia Pacific, Sydney)**, theo URL của website. Bật MFA cho tài khoản root và làm việc bằng IAM user, không dùng root.

### IAM role cho Lambda
Lambda chỉ cần hai quyền: đọc bảng LegalArticles và ghi log. Thay phần giữ chỗ bằng account ID và region của bạn.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ReadLegalArticles",
      "Effect": "Allow",
      "Action": [
        "dynamodb:Scan",
        "dynamodb:Query",
        "dynamodb:GetItem"
      ],
      "Resource": "arn:aws:dynamodb:ap-southeast-2:<ACCOUNT_ID>:table/LegalArticles"
    },
    {
      "Sid": "CreateLogGroup",
      "Effect": "Allow",
      "Action": "logs:CreateLogGroup",
      "Resource": "arn:aws:logs:ap-southeast-2:<ACCOUNT_ID>:*"
    },
    {
      "Sid": "WriteLogs",
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogStream",
        "logs:PutLogEvents"
      ],
      "Resource": "arn:aws:logs:ap-southeast-2:<ACCOUNT_ID>:log-group:/aws/lambda/legal-ai-chat-lambda:*"
    }
  ]
}
```

Gắn thêm managed policy **AWSLambdaBasicExecutionRole** để Lambda ghi được log vào CloudWatch.

*[Hình: IAM role có managed policy AWSLambdaBasicExecutionRole]*

### Tài khoản Groq và API key
**Tạo tài khoản và truy cập Groq Console**
1. Truy cập console.groq.com và đăng nhập (hoặc đăng ký tài khoản mới).
2. Sau khi đăng nhập, bạn sẽ thấy trang Dashboard của Groq Console.

*[Hình: Trang Dashboard của Groq]*

Trang Dashboard hiển thị lượng Token Usage trong 30 ngày gần nhất. Các lối tắt Playground, Docs và Manage Team giúp bạn chat thử với mô hình, xem tài liệu và quản lý thành viên.

**Tạo API Key**
1. Ở thanh menu phía trên bên phải, chọn **API Keys**.
2. Tại trang API Keys, bảng hiển thị "No keys" vì chưa có key nào. Chọn **Create API Key** ở góc phải.
3. Trong hộp thoại Create API Key:
   - **Display Name:** đặt tên gợi nhớ cho key, tối đa 50 ký tự.
   - **Expiration:** chọn thời hạn của key.
4. Chọn **Submit**.

*[Hình: Trang API Keys]*
*[Hình: Hộp thoại Create API Key]*

Hệ thống hiển thị API key dạng `gsk_...`. Chọn **Copy** để sao chép key.

> **Lưu ý:** key chỉ hiển thị một lần. Hãy lưu ngay vào nơi an toàn, vì sau khi đóng cửa sổ bạn sẽ không xem lại được.

*[Hình: API key vừa được tạo]*

Chọn **Done** để hoàn tất.

**Chọn model trong Playground**
1. Trên thanh menu, chọn **Playground**.
2. Ở ô chọn model phía trên, chọn model cần dùng. Trong bài này là **qwen/qwen3.8-27b**.
3. Chọn **View code** (khi đang mở sẽ hiện Hide code) để xem đoạn code mẫu gọi API đúng với model đã chọn.

*[Hình: Chọn model trong Playground]*

### Danh mục tài nguyên
| Tài nguyên | Tên | Ghi chú |
|---|---|---|
| S3 bucket | ai-legal-assistant-frontend-hau | Static website hosting |
| DynamoDB | LegalArticles | Cơ sở tri thức |
| Lambda | legal-ai-chat-lambda | Python |
| API Gateway | LegalChatAPI | Endpoint công khai cho website gọi |

### Cảnh báo chi phí
Tạo AWS Budget có cảnh báo email **trước khi xây dựng bất cứ thứ gì**. Mục tiêu của dự án là $0 trong Free Tier, và cảnh báo giúp phát hiện bất thường sớm.

**Mở trang Budgets**
1. Trong AWS Management Console, gõ **Billing and Cost Management** vào ô tìm kiếm rồi nhấn Enter.
2. Ở menu bên trái, chọn **Budgets**.
3. Chọn **Create budget** ở góc phải.

*[Hình: Trang Budgets, danh sách trống (0 budgets)]*

**Chọn loại budget**
- **Budget setup:** chọn **Use a template (simplified)**, tức là dùng cấu hình khuyến nghị có sẵn. Tùy chọn Customize (advanced) cho phép chỉnh chi tiết hơn nhưng không cần thiết ở đây.
- **Template:** chọn **Zero spend budget**, tức là báo ngay khi chi tiêu vượt $0.01. Các template khác như Monthly cost budget, Savings Plans hay Reservation không phù hợp với mục tiêu $0.
- **Billing View** là tùy chọn, có thể bỏ qua.
- Kéo xuống cuối trang và chọn **Next**.

*[Hình: Chọn template Zero spend budget]*

**Đặt tên và email nhận cảnh báo**
- **Budget name:** giữ tên mặc định hoặc đặt tên gợi nhớ hơn, ví dụ LegalRAG-Zero-Spend.
- **Email recipients:** nhập email nhận cảnh báo. Có thể nhập nhiều email, cách nhau bằng dấu phẩy (tối đa 10). Ô này sẽ báo lỗi "Enter a valid email address" khi còn trống, nên hãy nhập email thật của bạn.
- **Scope:** All AWS services, áp dụng cho toàn bộ dịch vụ trong tài khoản.
- Template settings giữ mặc định (có thể chỉnh sau).
- Chọn **Create budget**.

*[Hình: Đặt tên budget và nhập email nhận thông báo]*

**Kết quả**
Budget được tạo thành công và ở trạng thái **Healthy**. Cột Budget hiển thị $1.00, đây là mức nền của template, còn ngưỡng cảnh báo vẫn là $0.01.

*[Hình: Budget đã tạo, trạng thái Healthy]*

### Tài liệu pháp luật
Nguồn tham chiếu là Nghị định 13/2023/NĐ-CP. Trước khi demo, hãy kiểm tra văn bản nào đang có hiệu lực và có luật mới sửa đổi hoặc thay thế một phần nghị định hay không.
