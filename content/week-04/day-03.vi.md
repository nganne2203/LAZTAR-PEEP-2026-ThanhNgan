+++
title = "Ngày 03 - 07/10/2026 (Remote)"
weight = 3
+++

# Báo cáo ngày 03

## 1. Mục tiêu hôm nay

Hôm nay em tập trung hoàn thiện các nghiệp vụ trả hàng, kiểm kê và báo cáo hạn dùng ở backend, đồng thời tích hợp các luồng xuất kho, trả hàng, kiểm kê và báo cáo tồn kho trên frontend.

## 2. Hoàn thiện backend

- Hoàn thiện backend trả hàng: đối chiếu với đơn hàng gốc, giới hạn số lượng trả cộng dồn, chống tiếp nhận trùng, đồng thời hỗ trợ danh sách và biên bản trả hàng.
- Hoàn thiện backend kiểm kê: hỗ trợ danh sách, lọc, hủy đợt kiểm kê và duyệt chênh lệch; khóa các thao tác tồn kho trong những trường hợp cần thiết để bảo đảm dữ liệu nhất quán.
- Chuẩn hóa báo cáo hạn dùng: xử lý theo ngày lịch Việt Nam, phân nhóm cảnh báo, đếm lô duy nhất và hỗ trợ phân trang.

## 3. Tích hợp frontend

- Tích hợp luồng xuất kho gồm tạo đơn, FEFO và giữ hàng, xử lý thiếu hàng hoặc đổi hàng, picking và đóng gói.
- Tích hợp trả hàng và QC, bao gồm quota trả, chi tiết, lịch sử, hủy và đảo phiếu.
- Tích hợp kiểm kê với các thao tác tạo đợt, nhập số đếm, gửi kết quả, duyệt hoặc từ chối và hủy.
- Tích hợp ma trận tồn kho, dashboard và thông báo hạn dùng, cùng thẻ kho.

## 4. Kết quả và tổng kết

Các đầu việc backend và frontend được nêu trong kế hoạch hôm nay đã hoàn thành. Những luồng nghiệp vụ chính từ xuất kho, trả hàng, kiểm kê đến theo dõi tồn kho và hạn dùng đã được kết nối giữa giao diện và backend.
