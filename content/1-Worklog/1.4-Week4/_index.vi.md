---
title: "Nhật ký Tuần 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu tuần 4:

* Code Lambda tìm kiếm ngữ nghĩa (`vector-search`): đối chiếu vector câu hỏi với vector tài liệu trong RDS.
* Thiết kế Prompt chuẩn để ép LLM chỉ trả lời dựa trên tài liệu cung cấp, không bịa đặt thông tin.
* Cấu hình VPC cho Lambda ở phần hỏi đáp để có thể truy vấn được RDS (`pgvector`) — ghi chú **CẦN VPC** từ bảng phân công.
* Phối hợp fix lỗi multi-tenancy ảnh hưởng tới dữ liệu vector theo từng người dùng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2-3 | - Code Lambda `vector-search`: nhận câu hỏi từ người dùng, gọi Amazon Bedrock (Titan Embed) tạo vector câu hỏi <br> - Viết logic tính toán độ tương đồng (cosine similarity) giữa vector câu hỏi và vector tài liệu đã lưu trong RDS bằng truy vấn `ORDER BY embedding <=> query_vector LIMIT k`, trích xuất top-k chunk liên quan nhất làm ngữ cảnh | 13/07/2026 | 14/07/2026 | [pgvector – Querying](https://github.com/pgvector/pgvector#querying) |
| 4 | - Phát hiện lỗi: Lambda `vector-search` không kết nối được RDS vì RDS nằm trong private subnet không có route ra ngoài <br> - Nghiên cứu và cấu hình để Lambda "chui" vào VPC (gắn Subnet + Security Group tương ứng RDS) theo đúng ghi chú **CẦN VPC** trong bảng phân công, test lại kết nối thành công <br> - Đối chiếu chi phí: xác nhận không cần NAT Gateway cho riêng Lambda này vì chỉ cần gọi RDS nội bộ trong VPC, không cần ra internet | 15/07/2026 | 15/07/2026 | [Configuring a Lambda function to access resources in a VPC](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html) |
| 5 | - Thiết kế Prompt chuẩn cho LLM ở Amazon Bedrock: cấu trúc gồm system instruction (chỉ trả lời dựa trên ngữ cảnh cung cấp, nếu không tìm thấy thì báo không có thông tin), phần chèn các chunk ngữ cảnh, và câu hỏi người dùng <br> - Test thử với vài câu hỏi "đánh lừa" (hỏi ngoài phạm vi tài liệu) để kiểm tra Prompt có ép được LLM từ chối bịa đặt thông tin hay không | 16/07/2026 | 16/07/2026 | [Prompt engineering guidelines – Amazon Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/prompt-engineering-guidelines.html) |
| 6 | - Phối hợp fix lỗi rò rỉ dữ liệu đa người dùng (multi-tenancy) ở phần thuộc phạm vi mình phụ trách: bổ sung điều kiện lọc `WHERE user_id = :user_id` (và `document_id IN (...)` khi có chọn tài liệu cụ thể) vào truy vấn `vector-search`, tránh trả về ngữ cảnh của người dùng khác <br> - Test thực tế với 2 tài khoản, xác nhận mỗi người chỉ nhận được ngữ cảnh từ tài liệu của chính mình | 17/07/2026 | 17/07/2026 | |
| 7 | - Ghép nối `ChatbotRAG` (Lambda điều phối) với `vector-search` và Bedrock (LLM), chạy thử toàn bộ luồng hỏi đáp end-to-end lần đầu tiên với dữ liệu thật <br> - Ghi nhận các câu trả lời chưa chính xác để tinh chỉnh Prompt/chunk size ở tuần sau | 18/07/2026 | 18/07/2026 | |


### Kết quả đạt được tuần 4:

* Hoàn thành Lambda `vector-search`: tạo vector câu hỏi và tìm kiếm ngữ nghĩa (cosine similarity) trong RDS PostgreSQL.
* Cấu hình thành công VPC cho Lambda ở phần hỏi đáp để truy vấn được RDS (`pgvector`), xác nhận không phát sinh thêm chi phí NAT Gateway.
* Thiết kế và test Prompt chuẩn giúp LLM trả lời bám sát tài liệu, hạn chế bịa đặt thông tin ngoài ngữ cảnh.
* Phối hợp fix lỗi rò rỉ dữ liệu đa người dùng ở phần truy vấn vector, đảm bảo cách ly dữ liệu theo từng người dùng.
* Chạy thử thành công luồng hỏi đáp RAG end-to-end lần đầu tiên (ChatbotRAG → vector-search → Bedrock LLM).