---
title: "Nhật ký Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu tuần 6:

* Rà soát và chỉnh sửa lại nội dung Workshop (mục 5) liên quan tới phần mình phụ trách (Tạo vector, Hỏi đáp).
* Cập nhật sơ đồ Lambda Modules cho đúng thực tế triển khai (`create-vector`, `vector-insert`, `vector-search`, `ChatbotRAG`).
* Bổ sung testcase còn thiếu cho phần chat RAG vào mục System Testing (5.5).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Rà soát và chỉnh sửa nội dung mục Workshop phần tạo vector và hỏi đáp cho rõ ràng, nhất quán với thuật ngữ chung của nhóm <br> - Bổ sung ví dụ cụ thể (đoạn code chunking, câu Prompt mẫu) vào phần còn mô tả chung chung | 27/07/2026 | 27/07/2026 | |
| 3 | - Rà soát lại nội dung Blog kỹ thuật liên quan tới RAG (nếu có phần mình đóng góp), góp ý cùng nhóm trước khi đăng lên Facebook AWS Study Group | 28/07/2026 | 28/07/2026 | <https://www.facebook.com/groups/awsstudygroupfcj> |
| 4 | - Cập nhật sơ đồ kiến trúc Lambda Modules trên draw.io cho đúng thực tế: bổ sung đầy đủ luồng `create-vector` → `vector-insert` (VPC) và `ChatbotRAG` → `vector-search` (VPC), đánh dấu rõ ranh giới VPC <br> - Gửi bản xem trước cho nhóm xác nhận sơ đồ khớp với thực tế triển khai <br> - Thêm các testcase test còn thiếu cho phần chat RAG (câu hỏi trong phạm vi tài liệu, câu hỏi ngoài phạm vi, câu hỏi nhiều tài liệu) bổ sung vào mục System Testing (5.5) | 29/07/2026 | 29/07/2026 | <https://htuan2800.github.io/fcj-report/5-workshop/5.1-workshop-overview/5.1.3--overall-aws-architecture/> |
| 5 | - Rà soát và chỉnh sửa lại nội dung báo cáo tổng thể phần mình phụ trách, sửa lỗi chính tả và diễn đạt, thống nhất định dạng bảng/thuật ngữ với các phần khác trong báo cáo | 30/07/2026 | 30/07/2026 | |
| 6 | - Tiếp tục bổ sung các phần nội dung còn thiếu liên quan tới pipeline RAG (giải thích lý do chọn Titan Embed, lý do tách Lambda theo VPC) | 31/07/2026 | 31/07/2026 | |
| 7 | - Rà soát lại toàn bộ phần mình phụ trách lần cuối trước khi bước sang tuần nộp Workshop | 01/08/2026 | 01/08/2026 | |


### Kết quả đạt được tuần 6:

* Rà soát và chỉnh sửa nội dung mục Workshop phần tạo vector và hỏi đáp cho rõ ràng, nhất quán hơn.
* Góp ý nội dung Blog kỹ thuật liên quan tới RAG trước khi đăng lên cộng đồng.
* Cập nhật sơ đồ Lambda Modules đúng thực tế triển khai, đã đối chiếu với nhóm.
* Bổ sung đầy đủ các test cho phần chat RAG vào mục System Testing (5.5).
* Rà soát, chỉnh sửa và hoàn thiện phần nội dung báo cáo do mình phụ trách trước khi bước sang tuần nộp Workshop.