---
title: "Nhật ký Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
### Mục tiêu tuần 3:

* Code Lambda `create-vector`: nhận văn bản đã OCR, gọi Amazon Bedrock để tạo Vector Embeddings.
* Phối hợp với nhóm hoàn thiện sơ đồ Kiến trúc Tổng quan trên AWS dùng ở Proposal và mục 5.1.3.
* Rà soát tiến độ, test chéo các phần liên quan (flow xác thực Frontend) do đồng đội thực hiện.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2-3 | - Code Lambda `create-vector`: nhận chuỗi văn bản (đầu ra từ Textract), chia nhỏ thành các đoạn (chunk) theo kích thước ký tự cố định có overlap <br> - Viết hàm gọi API `InvokeModel` của Amazon Bedrock (Titan Embed) cho từng chunk, xử lý response trả về vector 1.024 chiều <br> - Test thủ công với một tài liệu PDF mẫu, kiểm tra số lượng chunk và vector sinh ra có khớp không | 06/07/2026 | 07/07/2026 | [Amazon Bedrock – Titan Embeddings](https://docs.aws.amazon.com/bedrock/latest/userguide/titan-embedding-models.html) |
| 4 | - Phối hợp cùng nhóm hoàn thiện sơ đồ Kiến trúc Tổng quan trên AWS (mục 5.1.3), tập trung vẽ đúng luồng 2 Lambda mình phụ trách (`create-vector`, và Lambda tìm kiếm ngữ nghĩa dự kiến ở tuần sau) trong khối "Cổng giao tiếp & Điều phối" <br> - Đối chiếu sơ đồ với AWS Well-Architected Framework, xác nhận việc tách Lambda gọi Bedrock (không VPC) và Lambda insert RDS (có VPC) là hợp lý về chi phí | 08/07/2026 | 08/07/2026 | [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) |
| 5 | - Viết Lambda `vector-insert` (đặt trong VPC) nhận vector từ `create-vector` qua `lambda_client.invoke()`, ghi vào bảng `document_chunks` trên RDS PostgreSQL (`pgvector`) <br> - Test insert với vector giả lập, kiểm tra dữ liệu lưu đúng định dạng `vector(1024)` | 09/07/2026 | 09/07/2026 | |
| 6 | - Rà soát và test flow xác thực Frontend do đồng đội làm (Login/Register/Protected Route) để đảm bảo JWT trả về đúng định dạng, phục vụ việc Lambda phía AI sẽ xác thực request sau này <br> - Ghi nhận vấn đề lỗi lẫn session giữa các tab để nhóm fix ở tuần sau (không thuộc phạm vi Lambda AI nhưng ảnh hưởng gián tiếp tới việc test end-to-end) | 10/07/2026 | 10/07/2026 | |
| 7 | - Tham gia sự kiện cộng đồng "Cloud Architect x Meet Up" | 11/07/2026 | 11/07/2026 | |


### Kết quả đạt được tuần 3:

* Hoàn thành Lambda `create-vector`: chia chunk văn bản và gọi Amazon Bedrock tạo vector embedding thành công.
* Hoàn thành Lambda `vector-insert` (chạy trong VPC), ghi vector vào RDS PostgreSQL (`pgvector`) qua cơ chế invoke đồng bộ giữa 2 Lambda.
* Phối hợp hoàn thiện sơ đồ Kiến trúc Tổng quan trên AWS dùng ở Proposal và mục 5.1.3, đảm bảo phản ánh đúng phần Lambda mình phụ trách.
* Rà soát flow xác thực Frontend, xác nhận định dạng JWT phù hợp để tích hợp ở các Lambda AI/RAG.
* Tham gia sự kiện "Cloud Architect x Meet Up" (11/07/2026).