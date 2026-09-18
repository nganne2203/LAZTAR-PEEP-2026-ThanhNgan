
+++
title = "Ngày 03 - 17/09/2026 (Remote)"
weight = 3
+++

# Báo cáo ngày 03

**Hình thức làm việc:** Remote
**Dự án:** Landing page StudyFlow AI

## A. Công việc thực hành

### 1. Mục tiêu

Hôm nay tôi làm việc từ xa và thực hiện landing page cho StudyFlow AI. Đây là ý tưởng về một trợ lý học tập ứng dụng AI, giúp học sinh và sinh viên hiểu những khái niệm khó, tóm tắt tài liệu, luyện tập bằng câu hỏi, lập kế hoạch học và theo dõi tiến độ. Mục tiêu của tôi là chuyển ý tưởng sản phẩm thành một giao diện frontend có khả năng tương tác, hiển thị tốt trên nhiều thiết bị và phù hợp để đưa vào portfolio.

### 2. Xác định sản phẩm và lập kế hoạch UI/UX

- Xác định tên sản phẩm, tagline, nhóm người dùng mục tiêu, vấn đề cần giải quyết, giá trị cốt lõi, các tính năng và lời kêu gọi hành động trước khi viết giao diện.
- Sắp xếp luồng nội dung từ hero và phần giới thiệu sản phẩm đến demo tương tác, bản xem trước dashboard, bảng giá, FAQ và lời kêu gọi hành động cuối trang.
- Tạo wireframe dạng văn bản cho desktop và mobile, hệ thống thiết kế, quy tắc responsive, yêu cầu accessibility và kế hoạch triển khai trong tài liệu của dự án.
- Chọn phong cách SaaS hiện đại, gọn gàng với chữ dễ đọc, khoảng trắng rộng, thẻ bo góc, đường viền nhẹ và màu tím làm điểm nhấn. Các bản xem trước giao diện sản phẩm là trọng tâm hình ảnh của trang.

### 3. Triển khai landing page

- Xây dựng trang bằng Next.js App Router, React, TypeScript, Tailwind CSS, Motion và biểu tượng Lucide. Vì dự án hiện tại đã dùng Next.js, tôi tiếp tục dùng framework này thay vì cài thêm Vite hoặc React Router.
- Tách giao diện thành các component cho layout, từng section và thành phần UI dùng chung. Dữ liệu về tính năng, gói giá, nhận xét, FAQ và câu hỏi mẫu được quản lý riêng với kiểu dữ liệu TypeScript rõ ràng.
- Hoàn thành thanh điều hướng, hero có giao diện hội thoại, dải chủ đề học tập, phần nêu vấn đề, sáu thẻ tính năng, quy trình ba bước, bản xem trước dashboard, số liệu mẫu, ba nhận xét hư cấu, ba gói giá, FAQ, lời kêu gọi hành động cuối trang và footer.
- Tạo demo AI hoàn toàn ở frontend: chọn câu hỏi gợi ý hoặc nhập câu hỏi riêng, hiển thị trạng thái chờ và hiệu ứng gõ chữ, nhận phản hồi mẫu, chọn câu hỏi tiếp theo và đặt lại cuộc hội thoại. Demo không gọi dịch vụ AI thật.
- Thiết kế menu mobile và bố cục responsive cho hero, các thẻ, demo, dashboard, bảng giá và footer. Bổ sung cấu trúc heading hợp lý, điều khiển bằng bàn phím, trạng thái focus rõ ràng, trạng thái FAQ cho công cụ hỗ trợ đọc màn hình và hỗ trợ giảm chuyển động.
- Ghi rõ rằng số liệu, câu chuyện sinh viên, mức giá và dữ liệu dashboard chỉ mang tính minh họa.

### 4. Kiểm tra và xử lý vấn đề

- Chạy ESLint, kiểm tra kiểu TypeScript và production build thành công.
- Kiểm tra trang trên trình duyệt ở kích thước desktop và mobile. Thử menu, câu hỏi gợi ý, câu hỏi tự nhập, chức năng đặt lại demo, FAQ và kiểm tra không có tràn ngang ở màn hình rộng 390px.
- Điều chỉnh kích thước tiêu đề hero để không lấn vào bản xem trước sản phẩm; sửa biểu tượng mũi tên của nút kêu gọi hành động bị xuống dòng trên mobile.
- Lần build đầu phụ thuộc vào việc tải font từ mạng và Turbopack không thể khởi chạy worker trong môi trường bị giới hạn. Tôi chuyển sang bộ font hệ thống có sẵn và cấu hình production build dùng webpack.

## B. Tổng kết

### Những gì tôi học được

- Việc xác định sản phẩm và phác thảo wireframe trước giúp giao diện nhất quán hơn và giảm các quyết định cảm tính trong lúc lập trình.
- Server Component của Next.js phù hợp với nội dung tĩnh của landing page; demo tương tác, menu mobile, FAQ và animation cần Client Component.
- Tương tác nhỏ giúp landing page thể hiện sản phẩm rõ hơn, nhưng phải nói minh bạch khi câu trả lời và dữ liệu chỉ là mô phỏng.
- Thiết kế responsive cần được kiểm tra trên màn hình thật hoặc viewport hẹp, không chỉ thu nhỏ bố cục desktop.

### Khó khăn và cách giải quyết

- **Cân bằng giữa hero nổi bật và bản xem trước dễ đọc:** Tôi kiểm tra giao diện desktop rồi điều chỉnh kích thước chữ, khoảng cách và vị trí thẻ nổi.
- **Giữ trải nghiệm thuận tiện trên mobile:** Tôi cho các cột xếp chồng, rút gọn thanh điều hướng của dashboard, kiểm tra các nút và xác nhận trang không bị tràn ngang.
- **Trình bày đúng bản chất của demo AI:** Tôi dùng phản hồi mẫu chạy cục bộ, thông báo rõ giới hạn với chủ đề chưa hỗ trợ và nêu rằng demo không tải lên hoặc lưu tài liệu học tập.

## URL PAGE

- Repository dự án: [StudyFlowAI trên GitHub](https://github.com/nganne2203/StudyFlowAI)
- Public preview: [StudyFlowAI on Vercel](https://studyflowai-eta.vercel.app)
