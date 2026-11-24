---
title: "5.3 Giai đoạn 1: Thiết lập Prompt và cơ chế RAG"
date: 2026-11-24
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

### Tổng quan
| Mục | Nội dung |
|---|---|
| Mục đích | Định hình cách mô hình ngôn ngữ nhận và xử lý dữ liệu pháp lý trước khi viết code. |
| Dịch vụ AWS | Không (thiết kế; kiểm thử trên Groq Playground) |
| Đầu ra | System prompt và mẫu prompt dùng trong Lambda |

### 5.3.1 Xây dựng System Prompt định hướng vai trò
**Mục tiêu:** Buộc mô hình đóng vai chuyên gia tư vấn pháp luật về các quy định tại Việt Nam, như Nghị định 13/2023/NĐ-CP.

**Các bước**
1. Viết câu định nghĩa vai trò (chuyên gia luật dữ liệu cá nhân Việt Nam).
2. Yêu cầu trả lời bằng tiếng Việt và nêu rõ điều luật đã sử dụng.
3. Thêm disclaimer: câu trả lời mang tính sơ bộ, không phải tư vấn pháp lý chính thức.

**Kiểm tra:** mô hình trả lời đúng vai trò và giọng điệu mong muốn.

### 5.3.2 Thiết lập ràng buộc ngữ cảnh
**Mục tiêu:** Buộc mô hình chỉ trả lời dựa trên văn bản pháp luật lấy từ cơ sở dữ liệu.

**Các bước**
1. Thêm quy tắc nghiêm ngặt: chỉ trả lời dựa trên văn bản pháp luật được cung cấp, không bịa đặt hay suy diễn ngoài nguồn.
2. Thêm phương án dự phòng: nếu văn bản được cung cấp không đủ, phải nói rõ là chưa đủ căn cứ.
3. Kiểm thử bằng câu hỏi ngoài phạm vi, ví dụ câu hỏi về thuế.

**Kiểm tra:** câu hỏi ngoài phạm vi nhận câu trả lời "chưa đủ căn cứ" thay vì một câu trả lời bịa đặt.

### 5.3.3 Xác định cấu trúc dữ liệu đầu vào
**Mục tiêu:** Quyết định cách Lambda đưa dữ liệu từ DynamoDB vào prompt gửi đi.

**Các bước**
1. Định dạng mỗi điều luật truy xuất thành một khối có nhãn (số điều và nội dung).
2. Đặt ngữ cảnh luật trước câu hỏi của người dùng trong message.
3. Giới hạn số lượng và độ dài điều luật để nằm trong giới hạn rate và token của mô hình.

*[Hình: Cấu trúc prompt gồm system prompt, ngữ cảnh luật và câu hỏi]*

**Kiểm tra:** prompt in ra có đủ ba phần, đúng thứ tự.
