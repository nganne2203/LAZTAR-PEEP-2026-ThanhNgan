+++
title = "Ngày 01 - 21/9/2026 (On-site)"
weight = 1
+++

# Báo cáo ngày 01

## 1. Mục tiêu học tập hôm nay

Hôm nay em tập trung tìm hiểu bối cảnh dự án và mô hình kinh doanh của hệ thống Mini-WMS trước khi bắt đầu triển khai tính năng nào. Mục tiêu của em là hiểu rõ quy trình kho end-to-end, mục tiêu dự án, cấu trúc team và các ràng buộc kỹ thuật để có thể làm việc hiệu quả với một đội gồm 5 người.

## 2. Những gì em đã làm

- Đọc sơ đồ tổng quan dự án FreshLink Produce và tìm hiểu mục đích kinh doanh của Mini-WMS.
- Xem lại luồng vận hành kho chính: nhận hàng → cất hàng → phân bổ tồn → soạn hàng → đóng gói → giao hàng → trả hàng.
- Phân tích 8 quy tắc nghiệp vụ cốt lõi của kho mà hệ thống bắt buộc phải tuân thủ.
- Tìm hiểu cách chia team và vai trò gợi ý: 2 Backend, 2 Frontend, 1 BA/QA, với nhiệm vụ rõ ràng.
- Nắm được stack công nghệ: NestJS, PostgreSQL 16, Prisma, React + TypeScript + Next.js, Docker Compose và GitHub Actions.
- Xem lại lộ trình 5 tuần và sản phẩm mong đợi ở từng giai đoạn.
- Tìm hiểu nguyên tắc “một đầu vào duy nhất” cho thay đổi tồn kho và vì sao không được cập nhật trực tiếp vào bảng tồn kho.

## 3. Kiến thức đã học

- Dự án là một demo nội bộ mô phỏng hệ thống quản lý kho cho khách hàng giả định FreshLink Produce.
- Đây không chỉ là ứng dụng CRUD đơn thuần, mà là hệ thống phản ánh logic vận hành thực tế và rủi ro nghiệp vụ của kho.
- Luồng nghiệp vụ chính bao gồm:
  - Nhận hàng
  - Cất hàng
  - Phân bổ tồn kho
  - Soạn hàng
  - Đóng gói
  - Giao hàng
  - Xử lý trả hàng
- Những quy tắc quan trọng nhất gồm:
  - Tồn khả dụng không đồng nghĩa với tồn vật lý.
  - Đơn vị tính phải quy đổi chính xác.
  - FEFO quan trọng hơn FIFO đối với hàng tươi.
  - Catch weight phải dựa trên số lượng thực tế, không chỉ số lượng đặt.
  - Thiếu hàng có thể xử lý bằng giao thiếu, đổi hàng hoặc hẹn giao sau.
  - Điều chỉnh tồn kho phải có người duyệt khác phê duyệt.
  - Import tồn đầu kỳ phải tránh nhập trùng.
  - Concurrency cần được xử lý đúng để tránh tồn kho âm.
- Dự án bắt buộc phải có một service sổ cái tồn kho duy nhất để mọi thay đổi tồn kho đi qua cùng một điểm kiểm soát.
- Mỗi team cần tuân thủ quy trình làm việc nghiêm ngặt, và dự án được thiết kế để đánh giá năng lực cá nhân chứ không chỉ code.

## 4. Hiểu về kiến trúc và mô hình triển khai

Theo mô tả dự án, trung tâm của hệ thống là InventoryLedgerService. Service này chịu trách nhiệm ghi lại mọi biến động tồn kho và duy trì lịch sử kế toán của số lượng hàng hóa. Điều này có nghĩa là mọi thay đổi tồn kho phải đi qua một điểm kiểm soát duy nhất, thay vì được sửa trực tiếp trên bảng tồn kho.

Cách làm này giúp team tránh mất đồng bộ dữ liệu, ngăn chỉnh sửa trái phép và dễ dàng kiểm toán lịch sử. Trong hệ thống kho, tồn kho không chỉ là một con số; nó là số dư cần có thể truy nguyên và giải thích được.

## 5. Những thách thức và lo ngại

- Dự án mang tính nghiệp vụ rất mạnh, nên em không thể chỉ tập trung vào code mà bỏ qua logic vận hành.
- Một số quy tắc đọc thì đơn giản nhưng triển khai lại khó, đặc biệt là FEFO, catch weight và xử lý đồng thời.
- Em cần chia công việc rõ ràng trong đội 5 người để cân bằng trách nhiệm giữa backend và frontend.
- Vì dự án được đánh giá dựa trên chất lượng nghiệp vụ, teamwork và chất lượng code, em cần chủ động báo sớm khi gặp chặn.

## 6. Kết luận

Ngày 01 của tuần 2 là một ngày định hướng quan trọng. Em đã hiểu rõ hơn về mục tiêu của dự án, logic nghiệp vụ và các ràng buộc kỹ thuật/luồng làm việc. Dự án này không đơn thuần là viết tính năng; nó là quá trình học cách vận hành một hệ thống kho thực tế và làm việc theo nhóm trong môi trường có áp lực nghiệp vụ thật.

Em thấy dự án này phù hợp với mô hình team 5 người vì domain khá phức tạp, quy trình end-to-end dài, và mỗi thành viên phải hiểu không chỉ lập trình mà còn logic kinh doanh, kỹ năng review và giao tiếp.

## 7. Phản ánh cá nhân

Ở các bước tiếp theo, em cần nghiên cứu kỹ 8 quy tắc nghiệp vụ của kho và chuyển chúng thành các yêu cầu kỹ thuật rõ ràng. Em cũng cần thống nhất với team về việc phân công, đặc biệt là module sổ cái tồn kho, để tránh logic trùng lặp hoặc cách triển khai không nhất quán.

## 8. Kỳ vọng với các bước tiếp theo

- Hiểu rõ tầm nhìn dự án và làm rõ luồng nghiệp vụ.
- Xác định ownership cho từng module trong đội 5 người.
- Bắt đầu chuẩn bị môi trường kỹ thuật và kiến trúc ban đầu.
- Xây dựng backlog cho sprint đầu dựa trên mục tiêu của tuần 2–3.
- Giữ tinh thần giao tiếp tích cực trong standup và review.
