+++
title = "Ngày 05 - 16/10/2026 (On-site)"
weight = 5
+++

# Báo cáo ngày 05

## 1. Mục tiêu hôm nay

Hôm nay em tập trung tối ưu hóa quy trình phân công xuất hàng bằng việc hợp nhất cho một nhân viên phụ trách trọn vẹn toàn bộ luồng xử lý; cập nhật backend để kiểm soát quyền chặt chẽ và duy trì tương thích ngược; đồng thời tái cấu trúc frontend với custom hooks/utils và chuẩn hóa toàn bộ constants trong hệ thống.

## 2. Gộp phân công xuất hàng (Soạn hàng → Đóng gói → Bàn giao/Xuất kho)

- Hợp nhất quy trình phân công: Cho phép chỉ định một nhân viên chịu trách nhiệm xuyên suốt từ khâu soạn hàng (picking), đóng gói (packing) đến bàn giao và xuất kho (handover/dispatch), giúp tinh gọn quy trình bàn giao nội bộ và nâng cao trách nhiệm cá nhân đối với từng đơn hàng.
- Tối ưu cấu trúc cơ sở dữ liệu: Không thêm bảng mới; tận dụng cấu trúc bảng và thực thể hiện có để quản lý thông tin phân công toàn luồng, tránh làm phình schema và tiết kiệm chi phí bảo trì CSDL.
- Tinh gọn giao diện phân công: Thay thế các trường phân công riêng rẽ bằng duy nhất một ô chọn người phụ trách cho toàn bộ đơn xuất, giúp quản lý thao tác nhanh chóng và giảm thiểu sai sót khi giao việc.
- Đồng bộ hiển thị và quyền thao tác: Giao diện tự động đồng bộ theo vai trò của người phụ trách; kích hoạt các nút hành động tương ứng với tiến độ đơn hàng và vô hiệu hóa các thao tác ngoài thẩm quyền.

## 3. Cập nhật backend và đảm bảo tương thích ngược

- Kiểm soát phân quyền xuyên suốt luồng: Bổ sung lớp kiểm tra chặt chẽ người phụ trách và quyền hạn ở từng bước chuyển tiếp trạng thái, đảm bảo chỉ nhân sự được phân công mới có quyền thực hiện các công đoạn từ soạn hàng đến xuất kho.
- Đảm bảo tương thích ngược với dữ liệu cũ: Xây dựng cơ chế xử lý tương thích cho các đơn xuất kho đã được phân công theo cách cũ (chia theo từng chặng độc lập), bảo đảm hệ thống vẫn đọc và xử lý chính xác mà không làm gián đoạn vận hành.
- Ràng buộc dữ liệu và kiểm tra hợp lệ: Thắt chặt các điều kiện chuyển đổi trạng thái đơn xuất, ghi nhận nhật ký điều chỉnh và ngăn chặn các hành động không hợp lệ khi trạng thái đơn không khớp.

## 4. Tái cấu trúc và tổ chức lại Frontend

- Bóc tách UI và logic nghiệp vụ: Rà soát các component liên quan đến xuất kho và quản lý đơn, tách phần logic xử lý trạng thái phức tạp, gọi API và kiểm tra dữ liệu ra khỏi tầng hiển thị (view).
- Xây dựng Custom Hooks theo tính năng: Đóng gói các luồng xử lý thành các custom hooks chuyên biệt (quản lý phân công đơn, theo dõi trạng thái phiếu xuất, thao tác xuất kho), giúp component gọn gàng, dễ bảo trì và dễ đọc hiểu.
- Tổ chức lại thư viện Utils dùng chung: Chuyển các hàm định dạng, tính toán và xử lý dữ liệu phụ trợ vào các module utils theo từng tính năng, tối ưu khả năng tái sử dụng và hỗ trợ viết unit test dễ dàng hơn.

## 5. Chuẩn hóa Constants và cấu hình hệ thống

- Tập trung hóa hằng số: Gom toàn bộ các giá trị hằng số phân tán rải rác trong mã nguồn vào các tệp constants dùng chung, xóa bỏ hoàn toàn magic strings và magic numbers.
- Quản lý trạng thái và Endpoint API: Quy chuẩn danh mục mã trạng thái của luồng kho và các đường dẫn gọi API vào các đối tượng hằng số có định kiểu rõ ràng.
- Chuẩn hóa giới hạn và thông số thời gian: Thiết lập cấu hình tập trung cho các giới hạn nhập liệu, ngưỡng số lượng, kích thước phân trang, thời gian chờ (debounce/timeout) và định dạng ngày giờ chuẩn xuyên suốt hệ thống.

## 6. Kết quả và tổng kết

Đã hoàn thành toàn bộ các đầu việc đề ra cho ngày hôm nay: gộp thành công luồng phân công xuất hàng cho một nhân viên xuyên suốt mà không cần thêm bảng mới; cập nhật backend kiểm tra quyền và giữ tương thích tuyệt đối với các đơn cũ; đồng bộ frontend với ô chọn duy nhất và tự động hóa theo quyền; hoàn tất tái cấu trúc frontend đưa logic sang custom hooks/utils theo từng tính năng và quy chuẩn hóa toàn bộ constants dùng chung trong hệ thống.
