+++
title = "Ngày 02 - 13/10/2026 (Remote)"
weight = 2
+++

# Báo cáo ngày 02

## 1. Mục tiêu hôm nay

Hôm nay em làm remote, tập trung hoàn thiện phân quyền duyệt phiếu trong quy trình kho và bổ sung cơ chế tự hủy cho các đơn chưa xuất kho khi quá hạn.

## 2. Phân quyền duyệt phiếu và thực hiện phân công

- Cho phép quản lý có quyền tại kho duyệt phiếu do chính mình tạo hoặc phiếu được phân công cho mình.
- Nhân viên được giao thực hiện phiếu chỉ có thể thao tác sau khi phiếu đã được duyệt; nhân viên không có quyền tự duyệt phiếu.
- Thêm tab **Đơn duyệt** tại **Tổng quan** để tập hợp các phân công đang chờ duyệt.
- Thêm tab **Đơn duyệt** tại **Xuất kho** để xem riêng các phiếu soạn hàng cần duyệt.
- Các kiểm thử về phân quyền và luồng thực hiện đã đạt.

## 3. Tự hủy đơn chưa xuất kho khi quá hạn

- Bổ sung cơ chế kiểm tra định kỳ mỗi phút đối với các đơn chưa xuất kho.
- Tự chuyển đơn sang trạng thái **Đã hủy** với lý do **“Quá hạn soạn đơn”** nếu đơn chưa được soạn đủ khi đã quá hạn.
- Tự chuyển đơn sang trạng thái **Đã hủy** với lý do **“Quá hạn hẹn giao”** nếu đã quá thời điểm hẹn giao.

## 4. Kết quả và tổng kết

Hoàn thiện quy tắc quản lý duyệt phiếu theo quyền tại kho, phân tách rõ quyền duyệt và quyền thực hiện, đồng thời bổ sung các tab **Đơn duyệt** phù hợp cho từng màn hình. Các kiểm thử phân quyền và luồng thực hiện đều đạt. Cơ chế tự hủy đơn chưa xuất kho cũng được bổ sung để xử lý các trường hợp quá hạn soạn đơn hoặc quá thời điểm hẹn giao, với trạng thái và lý do hủy tương ứng.
