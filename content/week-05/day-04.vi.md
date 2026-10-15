+++
title = "Ngày 04 - 15/10/2026 (On-site)"
weight = 4
+++

# Báo cáo ngày 04

## 1. Mục tiêu hôm nay

Hôm nay em tập trung hoàn thiện loạt cải tiến về kiểm soát phân quyền, luồng phân công và thực hiện phiếu xuất kho; đồng bộ giao diện và các component dùng chung; đồng thời chuẩn hóa các quy tắc validation hạn dùng, cảnh báo sức chứa, quản lý vị trí kiểm kê và tối ưu sắp xếp danh sách API.

## 2. Phân quyền và luồng xử lý sau phân công

- Đồng bộ UI theo quyền (permission): Tự động disable các nút thao tác khi thiếu quyền thực hiện; ẩn tab, menu chức năng và chặn truy cập trực tiếp qua URL nếu người dùng không có quyền xem.
- Khóa các bước đơn xuất ngoài thẩm quyền: Làm mờ các bước xử lý không được phép và hiển thị thông báo chuyển việc cho actor tiếp theo phụ trách.
- Quản lý giao việc và đổi người thực hiện: Khóa trường chọn nhân sự sau khi đã giao việc; bổ sung nút "Đổi phiếu", yêu cầu phải duyệt lại khi có thay đổi người thực hiện.
- Kiểm soát chặt chẽ quyền thực hiện sau phân công: Ràng buộc chỉ đúng nhân viên được giao, có đủ quyền và phiếu đã được duyệt mới được thao tác; bổ sung bộ lọc nhân viên theo từng công đoạn và kho phụ trách.
- Lọc danh sách công việc theo phân công: Nhân viên chỉ xem danh sách công việc được giao cho cá nhân; Quản lý xem toàn bộ trong phạm vi kho. Tách riêng phân công cho khâu soạn hàng, đóng gói và bàn giao.

## 3. Đồng bộ giao diện và chuẩn hóa component

- Thống nhất thao tác xem chi tiết: Quy chuẩn sử dụng nút icon hình con mắt, loại bỏ các nút và cột thao tác trùng lặp; mở trực tiếp màn hình chi tiết đầy đủ và hiển thị rõ họ tên người phụ trách.
- Đồng bộ trang Điều chuyển: Tái sử dụng component chung cho 2 tab, thống nhất đặt dưới phần mô tả; chuẩn hóa kích thước và icon cho nút "Tạo phiếu".
- Thống nhất component form chọn mặt hàng: Áp dụng chung cho các màn hình nhập/xuất, cất/chuyển, thay thế, nhà cung cấp, bảng giá, barcode và báo cáo.
- Chuẩn hóa badge trạng thái và thẻ thống kê: Việt hóa toàn bộ trạng thái, gán màu sắc trực quan theo ngữ nghĩa; giữ màu nhận diện ngay cả khi số liệu thống kê bằng 0; kiểm tra và tối ưu hiển thị trên cả desktop và mobile.

## 4. Ràng buộc nghiệp vụ kho và quy tắc kiểm tra dữ liệu

- Validation ngày sản xuất và hạn sử dụng: Áp dụng quy tắc NSX ≥ hôm nay, HSD ≥ NSX, chấp nhận NSX và HSD cùng ngày; duy trì cảnh báo từ bộ phận QC.
- Tinh gọn cảnh báo sức chứa: Chỉ hiển thị banner cảnh báo khi phát hiện vị trí vượt tải; hỗ trợ mở popup để theo dõi chi tiết và xử lý vị trí.
- Chuẩn hóa thông báo lỗi và kết quả cân: Validation chỉ hiển thị message lỗi ngắn gọn, loại bỏ thông báo khóa trùng lặp; kết quả cân mới nhất được đưa lên vị trí chính, lịch sử cân được thu gọn.
- Chuyển trường nhà vận chuyển thành dropdown: Bắt buộc chọn đơn vị vận chuyển trước khi thực hiện xuất hàng.
- Chặn chọn vị trí đang kiểm kê: Loại trừ các vị trí đang kiểm kê khỏi danh sách lựa chọn trong các luồng nhập/xuất, cất/chuyển, transit và trả hàng/QC; bổ sung cơ chế kiểm tra lại và chặn thực hiện đối với các phiếu đã mở sẵn từ trước.

## 5. Tối ưu truy vấn và sắp xếp dữ liệu danh sách

- Cập nhật logic sắp xếp mặc định cho các API lấy danh sách (GET ALL): Ưu tiên ngày tạo giảm dần (Created Date DESC), và ID giảm dần khi trùng thời điểm tạo.
- Hoàn tất kiểm tra và đảm bảo hoạt động nhất quán trên toàn bộ 19 API danh sách trong hệ thống.

## 6. Kết quả và tổng kết

Đã hoàn thành toàn bộ 15 task về tối ưu phân quyền, chuẩn hóa giao diện và siết chặt logic vận hành kho: từ việc kiểm soát quyền thực hiện sau phân công, lọc danh sách công việc, đồng bộ các component chi tiết/chọn mặt hàng/điều chuyển/badge thống kê, cho đến các ràng buộc dữ liệu về NSX-HSD, loại trừ vị trí kiểm kê, chuẩn hóa cân hàng và sắp xếp dữ liệu cho 19 API GET ALL.
