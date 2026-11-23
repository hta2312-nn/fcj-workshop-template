---
title: "Worklog Tuần 6"
date: 2026-10-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu Tuần 6:

- Thiết kế system prompt và các quy tắc ràng buộc ngữ cảnh (context rules) cho RAG.
- Thiết kế lược đồ dữ liệu (data schema) cho cơ sở tri thức pháp lý.

### Các công việc cần triển khai trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Đọc và nắm cấu trúc của Nghị định 13/2023/NĐ-CP <br> - Chọn lọc các điều khoản trọng tâm: <br>&emsp; + Dữ liệu cá nhân <br>&emsp; + Sự đồng ý <br>&emsp; + Quyền của chủ thể dữ liệu <br>&emsp; + Tiếp thị, quảng cáo <br>&emsp; + Xử lý vi phạm | 19/10/2026 | 19/10/2026 | <https://hcm-rules.awsfcaj.com/> |
| 3 | - Tạo tài khoản Groq, lấy API key và khám phá Playground <br> - Viết system prompt theo vai trò (role-based): <br>&emsp; + Trả lời bằng tiếng Việt <br>&emsp; + Trích dẫn rõ điều khoản <br>&emsp; + Thêm tuyên bố miễn trừ trách nhiệm (disclaimer) | 20/10/2026 | 20/10/2026 | Groq Docs |
| 4 | - Bổ sung các ràng buộc ngữ cảnh chặt chẽ và câu trả lời dự phòng (fallback) khi không đủ cơ sở pháp lý <br> - **Thực hành:** <br>&emsp; + Kiểm thử với câu hỏi ngoài phạm vi như vấn đề về thuế | 21/10/2026 | 21/10/2026 | Groq Docs |
| 5 | - Thiết kế schema `LegalArticles`: <br>&emsp; + `id`, `law_name`, `article_number`, `content`, `keywords` <br> - Định nghĩa cấu trúc ghép prompt (prompt assembly): <br>&emsp; + System prompt + ngữ cảnh pháp lý + câu hỏi, kèm giới hạn về số lượng điều khoản và độ dài | 22/10/2026 | 22/10/2026 | AWS Docs: DynamoDB |
| 6 | - **Thực hành:** <br>&emsp; + Kiểm thử các câu hỏi mẫu trên Playground (ví dụ: sử dụng số CCCD của khách hàng để quảng cáo) <br> - Tinh chỉnh và lưu lại mẫu prompt cuối cùng | 23/10/2026 | 23/10/2026 | Groq Docs |

### Kết quả đạt được Tuần 6:

- Nắm vững cấu trúc chính và các điều khoản trọng tâm của Nghị định 13/2023/NĐ-CP.
- Hoàn thiện system prompt theo vai trò cùng các quy tắc ràng buộc ngữ cảnh và cơ chế trả lời dự phòng.
- Thiết kế hoàn chỉnh lược đồ dữ liệu `LegalArticles` cho kho dữ liệu pháp lý.
- Định nghĩa, kiểm thử và chốt mẫu ghép prompt kèm các giới hạn ngữ cảnh.