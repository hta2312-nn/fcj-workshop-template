---
title: "Sự kiện 4"
date: 2026-11-24
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

**Tên sự kiện:** FCAJ Community Day

**Thời gian:** 08:30, ngày 31 tháng 10 năm 2026

**Địa điểm:** Tầng 26, Tòa nhà Bitexco, 02 Đường Hải Triều, Phường Sài Gòn, TP. Hồ Chí Minh

**Vai trò:** Người tham dự

# Báo cáo tổng kết: "Kiến trúc đám mây AWS, Software Factory và phát triển sự nghiệp"

## Mục tiêu sự kiện

Sự kiện nhằm mang đến cho người tham dự cái nhìn toàn diện về kiến trúc đám mây hiện đại, tập trung vào điện toán serverless và hệ thống bất đồng bộ. Thay vì chỉ trình bày lý thuyết, các phiên chia sẻ đưa ra bài học thực tế từ việc xây dựng "software factory" ở quy mô lớn.

Sự kiện cũng là cơ hội để học hỏi từ những người có kinh nghiệm về cách chuẩn bị cho sự nghiệp trong ngành đám mây, thu hẹp khoảng cách giữa trường đại học và doanh nghiệp, cũng như cách tham gia thực tập kỹ thuật và đóng góp cho mã nguồn mở.

## Diễn giả

* Thinh Nguyen – SYL Solution
* Henry Duc Bui – CloudThinker
* Hung Tran – NAB
* Dao Luong – FCAJ
* Khang Duong – FCAJ
* Tuan Tran – FCAJ

## Điểm nổi bật

### Xây dựng Software Factory ở quy mô lớn

Sự kiện bắt đầu bằng các bài học thực tế về cách xây dựng "software factory". Phần chia sẻ giúp mình hiểu những sai lầm phổ biến mà các đội nhóm thường gặp khi mở rộng quy mô phát triển phần mềm.

Phần này nhấn mạnh rằng để phát triển ở quy mô lớn, không chỉ cần mã nguồn tốt mà còn cần quy trình chuẩn hóa, tự động hóa và kinh nghiệm thực tế từ các đội nhóm đã thành công trong môi trường doanh nghiệp.

### Thu hẹp khoảng cách giữa giáo dục và ngành công nghiệp

Phần chia sẻ về giáo dục mang đến góc nhìn có giá trị về những gì sinh viên cần chuẩn bị trước khi bước vào ngành đám mây.

Phần này nhấn mạnh rằng kiến thức học thuật cần đi kèm với kỹ năng kỹ thuật thực hành, để thu hẹp khoảng cách giữa kỳ vọng của trường đại học và yêu cầu thực tế của doanh nghiệp.

### Thiết kế lại serverless với AWS Lambda

Một trong những phần kỹ thuật và thú vị nhất của sự kiện là đi sâu vào AWS Lambda Web Functions. Phiên chia sẻ giải thích cách hỗ trợ HTTP gốc và khả năng xử lý đồng thời 128 request đang thay đổi cách hiểu về điện toán serverless.

Phiên này cũng cho thấy việc loại bỏ chi phí của lớp adapter và tận dụng mô hình tính phí Active CPU Billing có thể tối ưu chi phí hiệu quả. Sự kiện có các benchmark hiệu năng trực tiếp so sánh serverless với Docker trên EC2 và ECS.

### Xây dựng hệ thống bất đồng bộ với Amazon SQS

Sự kiện kết nối các khái niệm kiến trúc với thiết kế hệ thống thực tế thông qua Amazon SQS. Mình hiểu vì sao các hệ thống hiện đại dựa nhiều vào xử lý bất đồng bộ để tách rời các dịch vụ và mở rộng hiệu quả.

Phiên chia sẻ đưa ra các mẫu thiết kế cụ thể và gợi ý thực tế để triển khai SQS trong ứng dụng thực tế.

### Phát triển sự nghiệp: thực tập và mã nguồn mở

Nửa sau của sự kiện tập trung vào phát triển nghề nghiệp. Mình được nghe chia sẻ về hành trình thực tập AWS kéo dài 3 tháng, đặc biệt là cách các dịch vụ AWS được áp dụng vào các dự án thực tế. Đây là lời khuyên rất cụ thể.

Ngoài ra, phiên về đóng góp mã nguồn mở hướng dẫn cách thực hiện lần đóng góp đầu tiên từ đầu, cách duy trì thói quen đều đặn, và cách tận dụng việc này để tăng tốc phát triển kỹ năng và sự nghiệp.

## Kết luận chính

### Góc nhìn kỹ thuật

* Kiến trúc serverless đang phát triển nhanh chóng. Các tính năng như đa đồng thời (multi-concurrency) và Active CPU Billing trong AWS Lambda giúp cải thiện đáng kể hiệu năng và hiệu quả chi phí.
* Các ứng dụng đám mây hiện đại và có khả năng mở rộng cần kiến trúc tách rời, khiến những công cụ như Amazon SQS trở nên thiết yếu để xử lý các luồng công việc bất đồng bộ một cách mượt mà.
* Xây dựng phần mềm có khả năng mở rộng đòi hỏi các thực hành chuẩn hóa ("software factory") thay vì chỉ viết mã độc lập.

### Tư duy thiết kế hệ thống

Bài học lớn nhất mình rút ra từ các phiên kiến trúc là tầm quan trọng của việc chọn đúng mô hình tính toán và mô hình truyền thông điệp. Trước khi triển khai một API hoặc một tác vụ xử lý, lập trình viên cần xem xét tác vụ nên là đồng bộ (dùng Lambda được tối ưu) hay bất đồng bộ (tách rời qua hàng đợi SQS) để tránh nghẽn cổ chai và đảm bảo độ tin cậy của hệ thống.

### Góc nhìn nghề nghiệp

Sự kiện cho mình thấy việc bước vào ngành đám mây đòi hỏi sự chuẩn bị chủ động. Kỹ năng kỹ thuật là rất quan trọng, nhưng kinh nghiệm thực tế có được qua thực tập, áp dụng AWS vào các dự án thực tế và đóng góp đều đặn cho cộng đồng mã nguồn mở mới là yếu tố thực sự tạo nên sự khác biệt của một ứng viên.

## Áp dụng vào dự án FCAJ

Kiến thức từ sự kiện có thể áp dụng trực tiếp và ngay lập tức vào dự án FCAJ của mình, nơi mình đang xây dựng một trợ lý RAG pháp lý serverless trên AWS.

Trước sự kiện, mình đã thiết lập hạ tầng cốt lõi bằng Amazon Bedrock Knowledge Bases, API Gateway, DynamoDB và một frontend React được host trên S3. Tuy nhiên, các phiên về AWS Lambda và Amazon SQS mang đến cho mình những ý tưởng mới để tối ưu kiến trúc:

* **Áp dụng tối ưu hóa AWS Lambda:** Hàm legal-ai-chat-lambda hiện xử lý các request từ API Gateway. Việc tìm hiểu về multi-concurrency và Active CPU Billing giúp mình biết cách tối ưu thời gian thực thi và quản lý chi phí tốt hơn khi nhiều người dùng cùng truy vấn trợ lý pháp lý.
* **Áp dụng Amazon SQS cho xử lý tài liệu:** Hiện tại, tài liệu pháp lý được lưu trong bucket S3 fcaj-raw-docs trước khi được xử lý thành các chunk. Phiên về SQS gợi ý cho mình việc tách rời luồng xử lý dữ liệu này. Mình có thể đặt một hàng đợi Amazon SQS giữa S3 và dịch vụ xử lý để tiếp nhận tài liệu bất đồng bộ. Điều này đảm bảo rằng khi hệ thống nhận một lô tài liệu pháp lý lớn, kiến trúc vẫn mở rộng được mà không bị nghẽn hay sập.

Sự kiện giúp mình chuyển tư duy từ "làm cho API chạy được" sang "thiết kế một kiến trúc serverless có khả năng mở rộng cao, tách rời và tiết kiệm chi phí".

## Trải nghiệm tham dự

### Học hỏi từ các diễn giả giàu kinh nghiệm

Sự kiện cho mình cơ hội học hỏi từ những người đã xây dựng các hệ thống lớn trong thực tế. Góc nhìn của họ giúp mình hiểu rõ hơn cách các dịch vụ AWS như Lambda và SQS được sử dụng trong môi trường doanh nghiệp thực sự, vượt ra ngoài các hướng dẫn cơ bản.

### Hiểu về kiến trúc trong thực tế

Thay vì chỉ học một dịch vụ làm gì, các benchmark trực tiếp và mẫu thiết kế kiến trúc cho mình thấy cách và lý do các công nghệ này được chọn để giải quyết bài toán khả năng mở rộng và chi phí trong môi trường production.

### Động lực cho sự nghiệp

Các phiên về thực tập và mã nguồn mở đặc biệt truyền cảm hứng. Chúng thúc đẩy mình không chỉ tập trung vào dự án FCAJ mà còn bắt đầu xây dựng một danh mục đóng góp công khai, nâng cao khả năng cộng tác và làm việc hiệu quả trong ngành công nghệ.

## Bài học rút ra

Bài học quan trọng nhất mình nhận được từ sự kiện là xây dựng phần mềm đám mây vững chắc đòi hỏi sự cân bằng giữa tính toán tối ưu (Lambda) và giao tiếp đáng tin cậy (SQS). Một kỹ sư đám mây giỏi không chỉ cần làm chủ việc triển khai kỹ thuật của các dịch vụ này, mà còn cần nuôi dưỡng thói quen học tập liên tục thông qua các dự án thực tế và đóng góp mã nguồn mở. Tư duy toàn diện này sẽ đồng hành cùng mình khi tiếp tục hoàn thiện trợ lý RAG pháp lý và phát triển sự nghiệp.

## Ảnh sự kiện

![Ảnh sự kiện 4, ảnh 1](../../images/4-EventParticipated/4.4-Event4/event4-01.png)

![Ảnh sự kiện 4, ảnh 2](../../images/4-EventParticipated/4.4-Event4/event4-02.jpeg)
