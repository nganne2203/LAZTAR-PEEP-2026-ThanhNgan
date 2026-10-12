+++
title = "Ngày 01 - 12/10/2026 (Remote)"
weight = 1
+++

# Báo cáo ngày 01

## 1. Mục tiêu hôm nay

Hôm nay em làm remote và triển khai tính năng `feat(wms): improve stock ledger, location UX and outbound shelf life`, tập trung cải thiện khả năng theo dõi tồn kho, luồng quản lý vị trí, cấu hình hạn sử dụng linh hoạt và độ an toàn của nghiệp vụ xuất hàng.

## 2. Thẻ kho và trải nghiệm quản lý vị trí

- Bổ sung trang Stock Ledger để tra cứu lịch sử biến động tồn kho song song với các bút toán kế toán đối ứng.
- Hỗ trợ lọc dữ liệu thẻ kho theo SKU, Lot và Bin; xuất CSV an toàn theo kho đang chọn, quyền của người dùng và bộ lọc hiện tại.
- Nâng cấp sơ đồ vị trí kho dạng cây theo cấu trúc Khu (Zone) > Kệ (Rack) > Ô kệ (Bin).
- Bổ sung panel tại vị trí để theo dõi sức chứa, tồn kho vật lý và lượng hàng đang được giữ tại đó.

## 3. Quy tắc hạn sử dụng và toàn vẹn dữ liệu kho

- Cho phép người dùng nhập số ngày hạn sử dụng tối thiểu còn lại cho từng dòng sản phẩm, trong khoảng 0 đến 365 ngày; nếu để trống thì mặc định là 2 ngày.
- Giữ nguyên giá trị 0 để hỗ trợ sản phẩm cần sử dụng gấp trong ngày, đồng thời vẫn từ chối hàng đã hết hạn khi nhận.
- Đồng bộ quy tắc kiểm tra hạn sử dụng giữa frontend, backend và ràng buộc database.
- Chặn xóa hoặc vô hiệu hóa kho khi còn tồn kho, hàng đang được giữ, hoặc chứng từ nhập, xuất, chuyển hàng hay kiểm kê chưa hoàn tất.

## 4. Xuất hàng, nhặt hàng và bù hàng

- Bổ sung thời hạn nhặt hàng `picking_due_at` cho luồng xuất hàng và khả năng theo dõi các tác vụ đã quá hạn.
- Bổ sung quy trình lập thỏa thuận thay thế sản phẩm thiếu tồn kho; lưu lý do, xác nhận của khách hàng, thời điểm thỏa thuận và hệ số quy đổi.
- Hỗ trợ điều chỉnh tồn nhanh từ dòng tồn kho hoặc chi tiết Bin, đồng thời giữ nguyên kiểm tra quyền, khóa khi đang kiểm kê và yêu cầu người duyệt độc lập.
- Bổ sung tem sản phẩm kích thước 50 × 30 mm và hỗ trợ in theo từng package; số lượng chưa in tiếp tục được giữ ở staging, đồng thời lưu lịch sử từng đợt giao để theo dõi.

## 5. Cải thiện thao tác và giao diện

- Chia các form nhập hàng, sản phẩm, vị trí, xuất hàng, trả hàng và dịch chuyển thành nhiều bước; đánh dấu xanh bước hợp lệ, giữ dữ liệu khi quay lại và kiểm tra thông tin trước khi lưu.
- Thu gọn khoảng trắng và sắp xếp section theo công việc vận hành. Bảng ưu tiên thông tin thường dùng, hiển thị gọn trong khung, hỗ trợ cuộn dọc và mở màn hình chi tiết thay vì phải kéo ngang.
- Thêm icon riêng để phân biệt khu, dãy, kệ và ô kệ; Việt hóa nhãn nghiệp vụ và trạng thái phê duyệt để dễ hiểu hơn.
- Lưu bộ lọc vị trí và đơn hàng trên URL; ngăn phản hồi tải về muộn hiển thị dữ liệu cũ sau khi đổi kho hoặc người dùng.

## 6. Kết quả và tổng kết

Hoàn thành các cải tiến WMS về theo dõi Stock Ledger, quản lý vị trí kho, cấu hình hạn sử dụng linh hoạt, bảo vệ toàn vẹn dữ liệu kho, và quy trình nhặt hàng cũng như thay thế sản phẩm thiếu tồn. Các form, bảng, tem nhãn, thao tác điều chỉnh tồn và trạng thái bộ lọc cũng được cải thiện để công việc kho rõ ràng và an toàn hơn.
