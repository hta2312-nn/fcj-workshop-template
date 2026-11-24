---
title: "Proposal"
date: 2026-11-24
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Legal RAG Platform: Hệ thống tư vấn pháp luật tự động cho Nghị định 13/2023/NĐ-CP
## Giải pháp AWS Serverless tích hợp LLM cho tra cứu và phân tích pháp lý theo thời gian thực

### 1. Executive Summary
Legal RAG Platform là hệ thống tư vấn pháp luật tự động, giúp người dùng và các thành viên trong nhóm nhanh chóng tra cứu, phân tích các quy định pháp luật phức tạp tại Việt Nam. Hệ thống tập trung vào Nghị định 13/2023/NĐ-CP về bảo vệ dữ liệu cá nhân. Nền tảng được xây dựng trên kiến trúc serverless hoàn toàn trên AWS và sử dụng mô hình ngôn ngữ lớn (LLM) từ Groq API (qwen/qwen3.8-27b). Câu trả lời được bám sát văn bản pháp luật thực tế, giúp giảm rủi ro AI bịa đặt thông tin. Nền tảng cũng giữ chi phí vận hành ở mức $0 nhờ nằm trong hạn mức AWS Free Tier.

### 2. Problem Statement
#### Vấn đề
- Các văn bản pháp luật như Nghị định 13/2023/NĐ-CP dài, nhiều nội dung chuyên môn và khó tra cứu thủ công đối với người không chuyên.
- Các công cụ AI đa dụng, như bản miễn phí của ChatGPT, thường thiếu kiến thức chuyên sâu về pháp luật Việt Nam. Câu trả lời thường chung chung và thiếu căn cứ pháp lý chính xác.
- Tự xây dựng một hệ thống AI riêng tốn kém về phần cứng và phức tạp trong vận hành.

#### Giải pháp
Nền tảng sử dụng quy trình RAG (Retrieval-Augmented Generation) tự động. Khi người dùng đặt câu hỏi, hệ thống tìm trong cơ sở dữ liệu các điều khoản liên quan nhất rồi đưa vào System Prompt. Sau đó, LLM tạo câu trả lời và trích dẫn rõ ràng các điều khoản đó.
- **Amazon DynamoDB** lưu trữ các điều khoản pháp luật đã trích xuất trong bảng LegalArticles.
- **AWS Lambda** xử lý logic backend, còn **Amazon API Gateway** cung cấp điểm cuối API ổn định.
- **Groq API** với mô hình qwen/qwen3.8-27b tạo ra câu trả lời rõ ràng, mạch lạc.
- **Amazon S3 Static Website** lưu trữ giao diện web, nơi người dùng tương tác qua khung chat.

#### Lợi ích và hiệu quả đầu tư (ROI)
- **Độ chính xác cao:** Câu trả lời bám sát văn bản pháp luật được cung cấp, minh bạch và có căn cứ.
- **Hiệu quả chi phí:** Kiến trúc serverless nằm trong AWS Free Tier, chi phí hàng tháng gần như bằng $0.
- **Khả năng mở rộng:** Kiến trúc tách rời giúp dễ dàng bổ sung các văn bản pháp luật mới vào DynamoDB trong tương lai, chẳng hạn Luật An toàn thông tin mạng hoặc Luật Công nghệ thông tin.

### 3. Solution Architecture
Hệ thống áp dụng kiến trúc serverless, kết nối khép kín giữa frontend, backend và LLM bên ngoài.

#### Dịch vụ AWS và công nghệ sử dụng
- **Amazon S3 Static Website:** Lưu trữ và phục vụ giao diện web tĩnh (index.html, CSS và JavaScript).
- **Amazon API Gateway:** Cung cấp HTTP/REST API công khai, xử lý CORS và chuyển các yêu cầu từ client đến Lambda.
- **AWS Lambda (Python):** Thực thi logic RAG, truy vấn DynamoDB và gọi Groq API.
- **Amazon DynamoDB (LegalArticles):** Lưu trữ các điều khoản pháp luật và hỗ trợ tra cứu theo từ khóa nhanh chóng.
- **Groq API (qwen/qwen3.8-27b):** Tạo và phân tích ngôn ngữ tự nhiên dựa trên ngữ cảnh pháp lý được cung cấp.

#### Thiết kế thành phần
- **Frontend:** Người dùng mở website trên S3 và nhập câu hỏi vào khung chat. Trình duyệt gửi HTTP POST chứa câu hỏi qua HTTPS đến API Gateway.
- **API Gateway:** Tiếp nhận yêu cầu, kiểm tra cấu hình CORS và chuyển dữ liệu đến hàm Lambda.
- **Truy xuất dữ liệu (DynamoDB):** Hàm `retrieve_legal_context` tìm trong bảng LegalArticles các điều khoản liên quan. Ví dụ, hệ thống có thể truy xuất quy định về xử lý vi phạm liên quan đến số căn cước công dân (CCCD) và dữ liệu cá nhân theo Nghị định 13.
- **Tăng cường ngữ cảnh và sinh câu trả lời (Groq API):** Lambda kết hợp câu hỏi của người dùng với ngữ cảnh pháp lý đã truy xuất thành một System Prompt có ràng buộc chặt chẽ, yêu cầu chỉ trả lời dựa trên ngữ cảnh được cung cấp. Sau đó, Lambda gọi Groq API.
- **Luồng phản hồi:** Groq trả kết quả về Lambda. Lambda định dạng lại dữ liệu theo chuẩn JSON và gửi qua API Gateway để hiển thị trong khung chat.

### 4. Technical Implementation
#### Các giai đoạn triển khai
- **Giai đoạn 1, thiết kế Prompt và cơ chế RAG:** Viết System Prompt định vai trò chuyên gia pháp lý và đặt ràng buộc ngữ cảnh, cấm bịa đặt thông tin.
- **Giai đoạn 2, triển khai Backend và cơ sở dữ liệu:**