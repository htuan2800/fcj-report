---
title: "Nhật ký Tuần 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### Mục tiêu tuần 1:

* Làm quen thành viên chương trình First Cloud AI Journey (FCAJ) và nắm quy trình làm việc trong kỳ thực tập.
* Nghiên cứu kiến thức nền tảng AWS Cloud, hạ tầng toàn cầu và các công cụ quản lý.
* Thực hành bảo mật tài khoản (MFA) và phân quyền IAM.
* Thảo luận nhóm, chốt đề tài Smart Docs AI và nhận vai trò phụ trách mảng **AI & RAG** (xử lý vector hóa tài liệu, thiết kế prompt, tìm kiếm ngữ nghĩa).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Làm quen thành viên FCAJ, đọc nội quy thực tập, nắm quy trình báo cáo và deadline nộp Worklog hàng tuần <br> - Xem "First Cloud Journey Kick off 2024", hướng dẫn vẽ kiến trúc AWS bằng Draw.io và làm Workshop; cài Hugo, làm quen tổ chức thư mục và cú pháp Markdown | 22/06/2026 | 22/06/2026 | [Kick off](https://www.youtube.com/watch?v=AQlsd0nWdZk&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=1) <br> [Hướng dẫn Draw.io](https://www.youtube.com/watch?v=l8isyDe-GwY&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=2) |
| 3 | - Học điện toán đám mây, điểm khác biệt của AWS, hạ tầng toàn cầu (Region/AZ/Edge Location), công cụ quản lý (Console/CLI/SDK) <br> - Tổng quan các nhóm dịch vụ AWS: Compute/Storage/Networking/Database — chú ý riêng nhóm dịch vụ AI/ML (Amazon Bedrock, SageMaker) vì đây sẽ là trọng tâm công việc của mình trong dự án <br> - Thực hành: tạo AWS Free Tier, bật MFA bảo vệ root account, đặt AWS Budget cảnh báo $5/tháng phòng quên tắt tài nguyên | 23/06/2026 | 23/06/2026 | [Khái niệm Cloud](https://www.youtube.com/watch?v=HxYZAK1coOI&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=4) <br> [AWS Free Tier](https://000001.awsstudygroup.com/vi/) |
| 4 | - Học IAM (Group/User/Policy/Role), nắm nguyên tắc least privilege — gắn Policy vào Group/Role thay vì trực tiếp vào User <br> - Thực hành: tạo IAM User/Role riêng cho việc thử nghiệm gọi API Amazon Bedrock, gắn Policy hạn chế chỉ cho phép `InvokeModel` thay vì full quyền Bedrock | 24/06/2026 | 24/06/2026 | [AWS IAM](https://000002.awsstudygroup.com/vi/) |
| 5 | - Thảo luận nhóm: chốt đề tài Smart Docs AI (RAG chatbot xử lý tài liệu) và bộ công nghệ (ReactJS, Python, AWS Serverless) <br> - Phân công vai trò: mình phụ trách mảng **AI & RAG**, cụ thể 2 giai đoạn: (1) tạo vector embedding cho tài liệu, (2) tìm kiếm ngữ nghĩa + thiết kế prompt cho LLM ở bước hỏi đáp | 25/06/2026 | 25/06/2026 | |
| 6 | - Đọc tổng quan tài liệu chính thức của Amazon Bedrock: danh sách model có sẵn (Titan Embed, Titan/Nova, Claude...), phân biệt model dùng để tạo embedding và model dùng để sinh câu trả lời (LLM) <br> - Đồng bộ ghi chú lên GitHub nhóm | 26/06/2026 | 26/06/2026 | [Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html) |
| 7 | - Tìm hiểu khái niệm RAG (Retrieval-Augmented Generation): pipeline tổng quát gồm embedding tài liệu → lưu vector store → truy vấn tương đồng → đưa ngữ cảnh vào prompt cho LLM <br> - Ghi chú so sánh sơ bộ các vector store khả dụng trên AWS (RDS + pgvector vs OpenSearch Serverless) để chuẩn bị đề xuất trong Proposal | 27/06/2026 | 27/06/2026 | [What is RAG? – AWS](https://aws.amazon.com/what-is/retrieval-augmented-generation/) |


### Kết quả đạt được tuần 1:

* Làm quen thành viên FCAJ, nắm quy trình làm việc trong kỳ thực tập.
* Nắm kiến thức nền tảng AWS Cloud: hạ tầng toàn cầu, các nhóm dịch vụ chính, đặc biệt là nhóm dịch vụ AI/ML.
* Tạo tài khoản AWS Free Tier, bật MFA, thiết lập AWS Budgets kiểm soát chi phí.
* Hiểu và thực hành phân quyền IAM theo nguyên tắc least privilege, áp dụng thử cho quyền gọi Bedrock.
* Chốt đề tài Smart Docs AI, nhận vai trò phụ trách mảng AI & RAG (tạo vector, tìm kiếm ngữ nghĩa, thiết kế prompt).
* Nắm khái niệm RAG và tổng quan Amazon Bedrock, chuẩn bị kiến thức nền cho các tuần triển khai tiếp theo.