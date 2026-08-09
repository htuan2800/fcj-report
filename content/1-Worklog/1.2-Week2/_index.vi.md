---
title: "Nhật ký Tuần 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
### Mục tiêu tuần 2:

* Đào sâu Amazon Bedrock: các model embedding khả dụng, giới hạn token, chi phí theo request.
* Nghiên cứu Amazon RDS PostgreSQL + extension `pgvector` làm vector store cho pipeline RAG.
* Tìm hiểu Amazon Cognito (song song với nhóm) để nắm luồng xác thực sẽ cần tích hợp với Lambda mảng AI.
* Phác thảo sơ đồ luồng "Giai đoạn 2 - Xử lý tài liệu" và "Giai đoạn 3 - Hỏi đáp" ở mức ý tưởng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2-3 | - Nghiên cứu chi tiết model **Titan Embed Text** trên Amazon Bedrock: số chiều vector đầu ra, giới hạn 8.192 token/lần gọi, cách tính chi phí theo token <br> - Viết thử script Python gọi `InvokeModel` API của Bedrock để chuyển một đoạn văn bản mẫu thành vector, kiểm tra định dạng response | 29/06/2026 | 30/06/2026 | [Amazon Bedrock – Titan Embeddings](https://docs.aws.amazon.com/bedrock/latest/userguide/titan-embedding-models.html) |
| 4 | - Nghiên cứu Amazon RDS & extension `pgvector`: cú pháp tạo cột kiểu `vector`, các loại index hỗ trợ tìm kiếm tương đồng (IVFFlat, HNSW) và phép đo khoảng cách (cosine, L2, inner product) <br> - So sánh sơ bộ `pgvector` trên RDS với OpenSearch Serverless (vector engine) — chọn `pgvector` vì chi phí thấp hơn và nhóm đã quen SQL | 01/07/2026 | 01/07/2026 | [pgvector GitHub](https://github.com/pgvector/pgvector) <br> [Hướng dẫn Amazon RDS](https://000005.awsstudygroup.com/vi/) |
| 5 | - Thử tạo bảng test có cột `vector(1024)` trên RDS PostgreSQL cục bộ (Docker), insert vài vector mẫu, chạy thử truy vấn `ORDER BY embedding <=> query_vector LIMIT 5` để hiểu cơ chế tìm kiếm cosine <br> - Ghi chú lại các tham số cần tinh chỉnh sau này: kích thước chunk văn bản, số chiều vector, ngưỡng similarity | 02/07/2026 | 02/07/2026 | |
| 6 | - Tìm hiểu Amazon Cognito (song song với phần của đồng đội phụ trách xác thực) để nắm cách Lambda phía AI sẽ nhận và xác thực JWT token của người dùng trước khi xử lý request <br> - Đọc tổng quan AWS KMS, ghi chú khả năng dùng để mã hóa dữ liệu vector/metadata nhạy cảm sau này | 03/07/2026 | 03/07/2026 | [Amazon Cognito](https://000081.awsstudygroup.com/vi/) |
| 7 | - Phác thảo sơ đồ ý tưởng cho 2 giai đoạn được phân công: **Giai đoạn 2 (Xử lý tài liệu)** — Lambda nhận văn bản đã OCR, gọi Bedrock tạo vector, lưu vào RDS; **Giai đoạn 3 (Hỏi đáp)** — Lambda nhận câu hỏi, tạo vector câu hỏi, tìm kiếm ngữ nghĩa trong RDS, ghép ngữ cảnh vào prompt gửi LLM <br> - Hoàn thiện, cập nhật Worklog tuần 1 và tuần 2 | 04/07/2026 | 04/07/2026 | Personal GitHub Repository |


### Kết quả đạt được tuần 2:

* Nắm chi tiết cách gọi Amazon Bedrock để tạo vector embedding (model Titan Embed, giới hạn token, chi phí).
* Nắm kiến thức nền tảng `pgvector` trên Amazon RDS PostgreSQL: kiểu dữ liệu vector, index, phép đo tương đồng.
* Thử nghiệm thành công truy vấn tìm kiếm cosine trên bảng vector mẫu chạy cục bộ.
* Nắm luồng xác thực Cognito ở mức cần thiết để tích hợp JWT vào Lambda phía AI.
* Phác thảo sơ đồ ý tưởng cho Giai đoạn 2 (Xử lý tài liệu) và Giai đoạn 3 (Hỏi đáp) — nền tảng để code trong các tuần tới.