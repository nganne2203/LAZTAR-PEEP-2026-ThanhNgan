
+++
title = "Ngày 03 - 17/09/2026 (Remote)"
weight = 3
+++

# Báo cáo ngày 03

- **Hình thức làm việc:** Remote
- **Dự án:** Landing page StudyFlow AI

## A. Công việc thực hành

### 1. Mục tiêu

Hôm nay tôi refactor source code của landing page StudyFlow AI và bổ sung phiên bản tiếng Việt. Mục tiêu là cho phép người dùng chuyển đổi giữa tiếng Anh và tiếng Việt nhưng vẫn dùng chung một bộ component dễ bảo trì. Tiếng Anh là ngôn ngữ mặc định.

### 2. Refactor source code

- Chuyển phần ghép các section của trang vào component LandingPage dùng chung. Hai route ngôn ngữ hiện sử dụng cùng một giao diện thay vì duy trì hai trang riêng biệt.
- Tạo module đa ngôn ngữ có kiểu dữ liệu TypeScript cho nội dung tiếng Anh và tiếng Việt. Các kiểu Locale và SiteCopy giúp xác định rõ cấu trúc nội dung cần có.
- Cập nhật navbar, hero, phần nêu vấn đề, sáu thẻ tính năng, demo tương tác, quy trình ba bước, dashboard mẫu, số liệu, nhận xét, bảng giá, FAQ, lời kêu gọi hành động cuối trang và footer để nhận nội dung theo ngôn ngữ qua props.
- Đưa nhãn giao diện, phần mô tả, dữ liệu mẫu, câu hỏi gợi ý, câu trả lời FAQ và phản hồi mô phỏng của demo vào dữ liệu ngôn ngữ. Cách này tách nội dung khỏi phần trình bày và giúp sửa copy về sau dễ hơn.
- Giữ nguyên phạm vi bản xem trước frontend. Câu trả lời AI, số liệu, nhận xét và mức giá vẫn là dữ liệu demo; không thêm backend hoặc API AI thật.

### 3. Phiên bản tiếng Việt và chuyển đổi ngôn ngữ

- Giữ landing page tiếng Anh ở URL gốc và thêm trang tiếng Việt tại /vi.
- Thêm nút chuyển EN/VI trên navbar, có trạng thái thể hiện ngôn ngữ hiện tại và vẫn hiển thị trên phần đầu trang responsive.
- Thiết lập thuộc tính ngôn ngữ HTML và metadata riêng cho từng route, đồng thời khai báo liên kết đến phiên bản ngôn ngữ còn lại cho công cụ tìm kiếm.
- Dịch nội dung landing page, nhãn dashboard, bảng giá, FAQ và demo tương tác. Demo nhận diện các từ khóa câu hỏi bằng tiếng Việt và trả về phản hồi mẫu bằng tiếng Việt.
- Điều chỉnh khoảng cách chữ và cách hiển thị thanh điều hướng để nội dung tiếng Việt dài hơn vẫn phù hợp trên màn hình nhỏ.

### 4. Kiểm tra

- ESLint chạy thành công, không có lỗi.
- Production build và bước kiểm tra kiểu TypeScript hoàn thành thành công.
- Kết quả build tạo hai route tĩnh: / cho tiếng Anh và /vi cho tiếng Việt.

## B. Tổng kết

### Những gì tôi học được

- Tập trung bản dịch trong một module có kiểu dữ liệu rõ ràng giúp giao diện đa ngôn ngữ dễ kiểm tra và bảo trì.
- Dùng chung cây component giúp bố cục của hai phiên bản không bị lệch nhau khi thay đổi giao diện.
- Đa ngôn ngữ không chỉ là dịch tiêu đề: nhãn form, nội dung hỗ trợ accessibility, metadata, phản hồi mẫu và khoảng cách responsive cũng cần được xử lý.

### Khó khăn và cách giải quyết

- **Nhiều đoạn tiếng Anh được viết trực tiếp trong component:** Tôi chuyển chúng sang nội dung theo ngôn ngữ truyền qua props và dùng chung LandingPage cho hai route.
- **Nội dung tiếng Việt thường dài hơn:** Tôi điều chỉnh letter spacing của heading và breakpoint của menu để nút chọn ngôn ngữ cùng thanh điều hướng có đủ chỗ.
- **Demo trước đây chỉ nhận diện từ khóa tiếng Anh:** Tôi bổ sung từ khóa tiếng Việt và phản hồi mẫu tương ứng, đồng thời giữ toàn bộ tương tác ở phía trình duyệt.

## URL PAGE

- Repository dự án: [StudyFlowAI trên GitHub](https://github.com/nganne2203/StudyFlowAI)
- Bản xem trước công khai: [StudyFlowAI trên Vercel](https://studyflowai-eta.vercel.app)
