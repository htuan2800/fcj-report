---
title: "Nhật ký Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
### Mục tiêu tuần 5:

* Tinh chỉnh chất lượng câu trả lời: kích thước chunk, ngưỡng similarity, cách ghép ngữ cảnh vào Prompt.
* Thiết lập CloudWatch Alarms giám sát riêng cho các Lambda mảng AI/RAG (`create-vector`, `vector-search`, `ChatbotRAG`).
* Tối ưu chi phí gọi Amazon Bedrock (giới hạn top-k, tránh gọi lặp không cần thiết).
* Hỗ trợ tích hợp bước test tự động (pytest) cho các hàm liên quan tới RAG vào CI/CD.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tinh chỉnh kích thước chunk (thử nghiệm 1.500 / 2.500 / 3.500 ký tự với overlap khác nhau), đo lại chất lượng câu trả lời trên cùng bộ câu hỏi test <br> - Thiết lập CloudWatch Alarm riêng cho Lambda `create-vector`, `vector-search`, `ChatbotRAG`: theo dõi số lỗi, thời gian xử lý (đặc biệt là độ trễ gọi Bedrock), số lần bị Throttle | 20/07/2026 | 20/07/2026 | [Using Amazon CloudWatch alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) |
| 3 | - Tối ưu ngưỡng similarity (cosine distance) và số lượng chunk (`top_k`) đưa vào Prompt: giảm số chunk dư thừa để giảm token đầu vào cho LLM, vừa giảm chi phí vừa hạn chế nhiễu ngữ cảnh <br> - Đo lại chi phí gọi Bedrock trước/sau khi tối ưu top_k trên cùng tập câu hỏi test | 21/07/2026 | 21/07/2026 | [Amazon Bedrock Pricing](https://aws.amazon.com/bedrock/pricing/) |
| 4 | - Đánh giá đổi model Bedrock cho phần sinh câu trả lời (thử `amazon.nova-lite-v1:0`), so sánh chất lượng và độ trễ với model cũ trên cùng bộ câu hỏi mẫu <br> - Cập nhật lại Prompt cho phù hợp với định dạng input/output của model mới | 22/07/2026 | 22/07/2026 | |
| 5 | - Rà soát và tinh chỉnh lại Prompt: bổ sung hướng dẫn trích dẫn tên tài liệu nguồn khi trả lời, xử lý trường hợp không tìm thấy chunk liên quan (trả lời "không có thông tin trong tài liệu" thay vì cố trả lời) <br> - Test lại 10 câu hỏi biên (câu hỏi mơ hồ, câu hỏi ngoài phạm vi, câu hỏi yêu cầu tổng hợp nhiều tài liệu) | 23/07/2026 | 23/07/2026 | |
| 6 | - Viết bộ test tự động (pytest) cho các hàm thuộc phạm vi mình phụ trách: hàm chia chunk, hàm tính cosine similarity, hàm build Prompt — tích hợp vào bước test của CodePipeline <br> - Đảm bảo bước test dừng sớm nếu bộ test của Lambda AI/RAG thất bại, trước khi build image | 24/07/2026 | 24/07/2026 | [Build specification reference – CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html) |
| 7 | - Họp nhóm: rà soát tiến độ, đọc chéo và góp ý phần báo cáo do mình viết <br> - Tham gia hackathon "FCAJ x Agentic AI Build Week powered by GenAI Fund" | 25/07/2026 | 25/07/2026 | |


### Kết quả đạt được tuần 5:

* Tinh chỉnh được bộ tham số chunk size/overlap và ngưỡng similarity giúp cải thiện rõ rệt chất lượng câu trả lời.
* Triển khai CloudWatch Alarms riêng cho các Lambda AI/RAG, chủ động phát hiện lỗi/độ trễ bất thường khi gọi Bedrock.
* Tối ưu chi phí gọi Amazon Bedrock bằng cách giảm top_k chunk đưa vào Prompt mà vẫn giữ chất lượng trả lời.
* Đánh giá thử model Bedrock mới, cập nhật Prompt tương thích.
* Hoàn thiện Prompt xử lý các trường hợp biên (không tìm thấy thông tin, câu hỏi mơ hồ) và trích dẫn nguồn tài liệu.
* Tích hợp bộ test tự động cho các hàm RAG vào CI/CD trên CodePipeline.
* Tham gia hackathon "FCAJ x Agentic AI Build Week powered by GenAI Fund" (25/07/2026).