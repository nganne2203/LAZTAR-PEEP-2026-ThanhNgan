+++
title = "Ngày 01 - 28/09/2026 (Remote)"
weight = 1
+++

# Báo Cáo Hằng Ngày - Ngày 01

## 1. Mục tiêu hôm nay

Hôm nay em rà soát lại bộ tài liệu nộp cuối cùng cho dự án và kiểm tra toàn bộ file bắt buộc trước khi upload lên Drive của công ty. Mục tiêu chính là đảm bảo repo, tài liệu hỗ trợ và yêu cầu audit log đều đầy đủ, rõ ràng và phù hợp với chuẩn quy định của dự án.

## 2. Tổng duyệt file trước khi nộp

Trước khi nộp lên Drive, em đã rà soát lại checklist để xác nhận từng file đã hoàn thiện, đặt tên đúng, và thống nhất với yêu cầu tài liệu của dự án.

### 2.1 Cấu trúc repo và source code

Dự án được lưu trong cùng một repository Git với 2 folder chính:

- backend/
- frontend/

Cấu trúc này rất quan trọng vì đây là một dự án có hai tầng riêng biệt nhưng nằm trong cùng một repo. Backend chịu trách nhiệm logic nghiệp vụ, tương tác database, kiểm tra stock flow và validation; Frontend chịu trách nhiệm giao diện, luồng thao tác người dùng và hiển thị dữ liệu.

### 2.2 Các file cần kiểm tra trước khi nộp

Bộ tài liệu cuối cần có các nội dung chính sau:

- Link repository và thông tin branch
- File README hướng dẫn setup và chạy dự án
- Thư mục source code backend
- Thư mục source code frontend
- Tài liệu thiết kế database hoặc ERD
- Tài liệu mô tả business flow
- Tài liệu sprint planning / kế hoạch dự án
- Nếu có, tài liệu mockup hoặc thiết kế UI
- Ghi chú kỹ thuật và quá trình triển khai
- Báo cáo tổng kết để nộp cho công ty

### 2.3 Checklist nộp tài liệu

Em rà soát từng file theo các tiêu chí sau:

- tên file rõ ràng, đúng chuẩn
- phiên bản và nội dung cập nhật
- không có file trùng lặp hoặc file cũ
- không thiếu tài liệu phụ trợ cần thiết
- không chứa dữ liệu khách hàng / nghiệp vụ sai hoặc nhạy cảm
- có mối liên hệ rõ với phạm vi dự án cuối cùng
- đã sẵn sàng để mentor và công ty review

Mục tiêu là tránh trường hợp nộp thiếu sót hoặc nộp bộ tài liệu khó review.

## 3. Yêu cầu audit log cho các bảng master

Trong quá trình tổng duyệt, em cũng kiểm tra lại yêu cầu audit log cho tất cả các bảng master trong hệ thống. Đây là quy tắc quan trọng về quản lý dữ liệu và truy nguyên.

### 3.1 Quy tắc với các bảng master

Mọi bảng master, trừ bảng stock_ledger, phải có các trường sau:

- created_at
- created_by
- updated_at
- updated_by

Những cột này giúp ta biết khi nào bản ghi được tạo, ai tạo, khi nào được cập nhật cuối cùng và ai cập nhật. Đây là yếu tố quan trọng để đảm bảo tính trách nhiệm dữ liệu, lịch sử hoạt động và khả năng đối chiếu sự cố.

### 3.2 Ngoại lệ: stock_ledger

Với bảng stock_ledger, chỉ cần có các trường sau:

- created_at
- created_by

Bảng này được xem là ledger ghi lịch sử biến động tồn kho, không được sửa trực tiếp sau khi tạo. Vì vậy, nó cần giữ nguyên lịch sử để đảm bảo tính toàn vẹn của dữ liệu tồn kho và hỗ trợ truy nguyên khi cần kiểm tra một giao dịch hay biến động cụ thể.

### 3.3 Tại sao quy tắc này quan trọng

Quy tắc audit log này hỗ trợ đúng yêu cầu nghiệp vụ: mọi thay đổi về tồn kho phải có thể truy nguyên, rõ nguồn gốc và không bị sửa mù mờ. Nó cũng giúp ngăn chặn thay đổi trái phép, ghi đè dữ liệu và sai lệch trong lịch sử vận hành kho.

## 4. Thông tin cho báo cáo mentor / công ty

Trong báo cáo cuối của công ty, thông tin mentor nên được thêm vào form báo cáo trước khi nộp.

- Mentor: Anh Huy
- Mục đích: thêm vào báo cáo công ty / phần review nộp hồ sơ
- Email: cần xác nhận lại với Anh Huy trước khi upload tài liệu lên Drive

Email này cần kiểm tra kỹ trước khi nộp để tránh thiếu thông tin hoặc nhập sai dữ liệu liên hệ trong báo cáo.

## 5. Cấu trúc dự án và phạm vi nộp

Dự án được quản lý trong cùng một repo với 2 folder chính:

- backend: phần logic server, database, validation và xử lý nghiệp vụ
- frontend: phần UI, màn hình, tương tác người dùng và hiển thị dữ liệu

Cấu trúc repo này cần được mô tả rõ trong hồ sơ nộp để reviewer có thể hiểu cách tổ chức dự án và trách nhiệm của từng phần.

## 6. Kết luận rà soát

Ngày hôm nay là ngày tổng duyệt cuối cùng trước khi upload tài liệu lên Drive. Bài học lớn nhất là một sản phẩm kỹ thuật không chỉ là code, mà còn là sự hoàn thiện của bộ tài liệu, tính rõ ràng của repo, độ chính xác của logic nghiệp vụ và khả năng truy nguyên của dữ liệu qua audit log.

Em sẽ tiếp tục duy trì cấu trúc repo, kiểm tra lại toàn bộ file cần thiết và đảm bảo bộ tài liệu cuối sẵn sàng cho việc nộp chính thức lên công ty.
