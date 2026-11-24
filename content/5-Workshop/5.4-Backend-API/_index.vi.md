---
title: "5.4 Giai đoạn 2: Backend, từ Database đến Lambda và API"
date: 2026-11-24
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

### Tổng quan
| Mục | Nội dung |
|---|---|
| Mục đích | Backend serverless truy xuất điều luật, gọi LLM và cung cấp API ổn định. |
| Dịch vụ AWS | DynamoDB, Lambda, API Gateway, CloudWatch |
| Đầu vào | HTTP POST chứa câu hỏi của người dùng |
| Đầu ra | JSON chuẩn chứa câu trả lời hoặc mã lỗi |
| Phụ thuộc | Prompt ở Giai đoạn 1; Groq API key |

### 5.4.1 Xây dựng Knowledge Base trên DynamoDB
**Mục tiêu:** Lưu các điều luật vào bảng mà Lambda có thể truy vấn.

**Tạo bảng DynamoDB LegalArticles**
1. Trong AWS Management Console, gõ **DynamoDB** vào ô tìm kiếm rồi nhấn Enter.
2. Ở menu bên trái, chọn **Tables**, sau đó chọn **Create table**.

*[Hình: Trang Tables và nút Create table]*

**Phần Table details**
- **Table name:** LegalArticles. Tên dài 3 đến 255 ký tự, chỉ gồm chữ, số, dấu gạch dưới (_), gạch ngang (-) và dấu chấm (.).
- **Partition key:** id, kiểu String. Đây là khóa chính dùng để định danh từng điều luật. DynamoDB băm giá trị này để biết lưu và tìm item ở đâu.
- **Sort key (tùy chọn):** để trống, vì bảng chỉ cần một khóa là id.
- Giữ cài đặt mặc định và chọn **Create table**.

*[Hình: Phần Table details và cài đặt mặc định]*

Sau vài giây, bảng LegalArticles chuyển sang trạng thái **Active**. Các bước sau sẽ thêm các điều luật của Nghị định 13/2023/NĐ-CP vào bảng này.

**Chuẩn bị IAM role cho Lambda**
1. Trong AWS Management Console, gõ **IAM** vào ô tìm kiếm rồi nhấn Enter.

*[Hình: Trang IAM Dashboard]*

Mục **Security recommendations** cho thấy tài khoản đã đạt hai khuyến nghị bảo mật: root user đã bật MFA và root user không có access key đang hoạt động. Đây là cách làm đúng: bật MFA cho root và làm việc bằng IAM user.

Mục **IAM resources** thống kê tài nguyên hiện có. Menu bên trái gồm Roles, Policies và IAM users. Chúng ta sẽ dùng **Roles** để tạo role cho Lambda.

1. Ở menu bên trái, chọn **Roles**. Trang này hiển thị danh sách các role của tài khoản. Role là một danh tính có các quyền cụ thể, dùng thông tin xác thực ngắn hạn và có thể được các thực thể tin cậy (như Lambda) đảm nhận (assume).
2. Chọn **Create role** ở góc phải.

*[Hình: Trang danh sách Roles]*

**Thiết lập role**
- **Trusted entity type:** chọn AWS service. **Use case:** chọn Lambda.
- **Permissions:** gắn managed policy **AWSLambdaBasicExecutionRole** để Lambda ghi được log vào CloudWatch, và thêm policy cho phép đọc bảng LegalArticles (chỉ cấp quyền tối thiểu cần thiết).
- **Role name:** đặt tên gợi nhớ, ví dụ legal-ai-chat-role.
- Chọn **Create role**.

*[Hình: Thiết lập role và policy đọc LegalArticles]*

**Truy xuất điều luật từ DynamoDB (retrieve_legal_context)**

*[Hình: Hàm retrieve_legal_context truy vấn DynamoDB]*

### 5.4.2 Lập trình hàm AWS Lambda (logic RAG và Groq API)
**Mục tiêu:** Truy xuất ngữ cảnh luật và sinh câu trả lời trong một hàm Python.

**Tạo hàm Lambda**
1. Trong AWS Management Console, gõ **Lambda** vào ô tìm kiếm rồi nhấn Enter.
2. Trang Functions hiển thị danh sách các hàm Lambda trong region hiện tại. Chọn **Create function** ở góc phải.
3. Ở trang Create function, chọn **Author from scratch**.

*[Hình: Trang Lambda và nút Create function]*
*[Hình: Chọn Author from scratch]*

- **Function name:** legal-ai-chat-lambda. Tên dài 1 đến 64 ký tự, không có khoảng trắng, chỉ gồm chữ, số, gạch ngang (-) và gạch dưới (_).
- **Runtime:** chọn **Python 3.12**.
- **Permissions:** mặc định Lambda tự tạo một execution role chỉ có quyền ghi log lên CloudWatch Logs. Vì hàm cần đọc thêm DynamoDB, ta sẽ dùng role đã tạo ở bước trước.

**Gắn execution role đã tạo**
1. Kéo xuống phần **Additional settings** và bật công tắc **Custom execution role**.
2. Khi bật, panel Configure custom execution role hiện ra bên phải. Mở danh sách **Execution role** và chọn **legal-ai-chat-role**.
3. Nếu muốn kiểm tra quyền của role, chọn **View role details in IAM**.
4. Chọn **Save**.

*[Hình: Bật Custom execution role]*
*[Hình: Chọn legal-ai-chat-role trong panel Configure custom execution role]*

Các tùy chọn khác như ARM64 architecture, Function URL, VPC và Durable execution giữ ở trạng thái tắt. Ta sẽ dùng API Gateway thay cho Function URL. Các cài đặt có biểu tượng riêng không thể thêm hoặc bỏ sau khi hàm được tạo. Các cài đặt còn lại có thể đổi sau.

Chọn **Create function**. Thông báo "Successfully created the function" xuất hiện.

*[Hình: Thông báo tạo hàm thành công]*

**Lập trình hàm Lambda (lambda_function.py)**

*[Hình: Mã lambda_function.py trong trình soạn thảo của Lambda]*

**Deploy code lên Lambda**
1. Sau khi dán code vào lambda_function.py, chọn **Deploy** để lưu và áp dụng code.
2. Thông báo màu xanh "Successfully updated the function legal-ai-chat-lambda" cho biết code đã được cập nhật. Nếu chưa bấm Deploy, Lambda vẫn chạy code cũ.

*[Hình: Nút Deploy]*
*[Hình: Thông báo deploy thành công]*

**Thêm biến môi trường GROQ_API_KEY**
Code đọc key từ biến môi trường GROQ_API_KEY, nên không ghi key trực tiếp trong code.
1. Chọn tab **Configuration**, rồi chọn **Environment variables** ở menu bên trái. Danh sách hiện đang trống.
2. Chọn **Edit**, sau đó chọn **Add environment variable** và điền:
   - **Key:** GROQ_API_KEY
   - **Value:** dán API key (gsk_...) đã copy từ Groq.
3. Chọn **Save**. Hệ thống hiện thông báo cập nhật thành công.

Biến GROQ_API_KEY đã được gắn vào hàm. Nếu thiếu biến này, hàm sẽ trả lỗi 500 "Thiếu cấu hình GROQ_API_KEY trên hệ thống", như đã viết trong code.

*[Hình: Biến môi trường GROQ_API_KEY sau khi lưu]*

**Tăng Timeout của hàm**
1. Ở tab Configuration, chọn **General configuration**, rồi chọn **Edit**.
2. Mặc định hàm có Memory 128 MB, Ephemeral storage 512 MB và Timeout chỉ 3 giây.
3. Đặt **Timeout: 0 min 30 sec**. Ba giây là quá ngắn, vì hàm phải quét DynamoDB, gọi Groq API và chờ mô hình sinh câu trả lời. Nếu quá thời gian, Lambda sẽ tự ngắt và client nhận lỗi.
4. Giữ nguyên Execution role là legal-ai-chat-role và Memory 128 MB là đủ cho bài này.
5. Kéo xuống cuối trang và chọn **Save**.

*[Hình: Cấu hình Timeout 30 giây]*

**Luồng xử lý bên trong hàm Lambda**

*[Hình: Sơ đồ luồng xử lý bên trong hàm Lambda]*

### 5.4.3 Cấu hình API Gateway và chuẩn hóa xử lý lỗi
**Mục tiêu:** Mở hàm Lambda qua endpoint HTTPS công khai mà trình duyệt được phép gọi.

**Các bước**
1. Tạo API (HTTP API) với route POST trỏ tới hàm Lambda.
2. Cấu hình CORS: Access-Control-Allow-Origin là `*`, các method POST và OPTIONS.
3. Xây dựng tầng xử lý lỗi trong Lambda, trả về các mã trong bảng dưới đây.
4. Deploy stage và ghi lại URL gọi API.

| Mã | Khi nào | Ý nghĩa với client |
|---|---|---|
| 400 | Dữ liệu không hợp lệ | Sửa lại request |
| 429 | Chạm giới hạn của Groq API | Chờ rồi thử lại |
| 502 / 504 | Lỗi hệ thống hoặc AI | Thử lại sau |

**Tạo HTTP API**
1. Trong AWS Management Console, gõ **API Gateway** vào ô tìm kiếm rồi nhấn Enter.

*[Hình: Trang chủ API Gateway]*

API Gateway là dịch vụ được quản lý hoàn toàn, giúp tạo, xuất bản, giám sát và bảo mật API ở mọi quy mô. Trong bài này, nó đóng vai trò cổng HTTPS công khai để trang web S3 gọi tới hàm Lambda.

2. Chọn **Create an API** ở khung Get started.
3. Ở trang Choose an API type, tìm thẻ **HTTP API** và chọn **Build**.

*[Hình: Chọn loại API HTTP API]*

HTTP API có độ trễ thấp, chi phí thấp, hỗ trợ sẵn CORS và tích hợp được với Lambda. Với bài này, HTTP API là đủ và rẻ hơn REST API.

**Bước 1: Configure API**
- **API name:** LegalChatAPI.
- **IP address type:** giữ IPv4.
- **Integrations:** chọn **Add integration**, sau đó chọn tích hợp **Lambda**.
  - **AWS Region:** chọn region của hàm Lambda.
  - **Lambda function:** chọn legal-ai-chat-lambda.
  - **Version:** giữ 2.0 (payload format version 2.0 của HTTP API).
- Chọn **Next**.

*[Hình: Đặt tên API LegalChatAPI]*
*[Hình: Thêm tích hợp Lambda]*

**Bước 2: Configure routes**
Route gồm hai phần: Method (phương thức HTTP) và Resource path (đường dẫn).
- **Method:** POST
- **Resource path:** /chat
- **Integration target:** legal-ai-chat-lambda
- Chọn **Next**.

*[Hình: Cấu hình route]*

**Bước 3: Define stages**
Stage là môi trường triển khai của API, ví dụ dev hoặc prod. Mặc định console tạo stage $default với **Auto-deploy** đang bật, nghĩa là mọi thay đổi sẽ tự được triển khai. Giữ mặc định và chọn **Next**.

**Bước 4: Review and create**
Kiểm tra lại toàn bộ cấu hình, sau đó chọn **Create**.
- API name: LegalChatAPI, IPv4.
- Integrations: legal-ai-chat-lambda (Lambda).
- Routes: /chat → legal-ai-chat-lambda.
- Stages: $default (Auto-deploy: enabled).

*[Hình: Màn hình Review trước khi tạo API]*

Khi tạo xong, thông báo "Successfully created API LegalChatAPI" xuất hiện.

**Cấu hình CORS**
CORS cho phép trang web ở một domain (website S3) gọi API ở domain khác (API Gateway). Nếu thiếu cấu hình này, trình duyệt sẽ chặn request.
1. Ở menu bên trái, mục **Develop**, chọn **CORS**. Ban đầu các mục ghi "No Origins/Headers/Methods are allowed", tức là chưa cho phép gì.
2. Chọn **Configure** và điền:
   - **Access-Control-Allow-Origin:** nhập `*` rồi chọn **Add** (cho phép mọi origin).
   - **Access-Control-Allow-Headers:** nhập `content-type` rồi chọn **Add**.
   - **Access-Control-Allow-Methods:** chọn POST và OPTIONS.
   - **Access-Control-Max-Age:** để 0. **Allow-Credentials:** để NO.
3. Chọn **Save**.

*[Hình: Cấu hình CORS]*

**Tạo stage và deploy**
1. Chọn **Deploy**, sau đó tạo stage **v1**.
2. Phần Stage details hiển thị Invoke URL có dạng `https://<api-id>.execute-api.<region>.amazonaws.com/v1`. Đây là địa chỉ gốc để gọi API.
3. Automatic Deployment của stage v1 đang **Disabled**, nên mỗi lần sửa cấu hình phải bấm Deploy thủ công.
4. Chọn **Deploy** và chọn stage v1.

*[Hình: Deploy stage v1]*

Thông báo "Successfully created deployment for LegalChatAPI" cho biết API đã được triển khai. URL đầy đủ để gọi hàm là:

`https://<api-id>.execute-api.<region>.amazonaws.com/v1/chat`

### 5.4.4 Kiểm thử Backend
**Mục tiêu:** Chứng minh backend hoạt động trước khi nối giao diện.

**Các bước**
1. Gửi POST bằng curl với một câu hỏi mẫu:

```bash
curl -X POST "<API_URL>" \
  -H "Content-Type: application/json" \
  -d '{"question": "Dùng CCCD để trao đổi mua bán có được không?"}'
```

2. Mở CloudWatch Logs và kiểm tra thời gian phản hồi, dữ liệu trả về và cấu trúc JSON.
3. Kiểm thử các trường hợp lỗi: câu hỏi rỗng (400) và, nếu có thể, trường hợp vượt giới hạn (429).

**Kiểm tra:** curl trả về câu trả lời có căn cứ, và log thể hiện đủ luồng xử lý.
