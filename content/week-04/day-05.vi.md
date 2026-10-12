+++
title = "Ngày 05 - 09/10/2026 (On-site)"
weight = 5
+++

# Báo cáo ngày 05

## 1. Mục tiêu hôm nay

Hôm nay em tập trung sửa các điểm còn thiếu trong giao diện kho và Stock Ledger cho buổi demo, cập nhật logic backend cho luồng nhận hàng linh hoạt hơn, và trình chiếu demo trực tiếp cho công ty để nhận feedback.

## 2. Cải thiện giao diện và chuẩn bị demo

- Thêm giao diện Stock Ledger còn thiếu để hiển thị biến động và số lượng tồn kho rõ ràng hơn.
- Cải thiện cách hiển thị kho để người xem dễ quét thông tin, với bố cục rõ ràng hơn, khoảng cách hợp lý và thứ bậc thông tin dễ theo dõi.
- Làm mịn phần tổng quan kho/tồn kho để buổi demo dễ hiểu hơn với các bên liên quan.
- Kiểm tra luồng từ đầu đến cuối trước khi demo để đảm bảo màn hình nhận hàng và màn hình tồn kho đồng bộ với logic nghiệp vụ thực tế.

## 3. Cập nhật logic backend

- Cập nhật logic nhận hàng để người dùng có thể chọn hạn sử dụng tối thiểu cho từng sản phẩm nhận, thay vì dùng quy tắc cứng 2 ngày.
- Giữ tùy chọn này có thể cấu hình theo sản phẩm hoặc theo luồng nhận hàng để phù hợp với từng loại hàng hóa và yêu cầu vận hành.
- Kiểm tra lại logic để đảm bảo quy tắc hạn sử dụng tối thiểu được áp dụng đúng trong quá trình nhận hàng và phản ánh đúng trên dữ liệu tồn kho sau đó.

## 4. Xác thực và hướng xử lý xóa kho còn hàng

- Xem xét vấn đề xóa kho khi kho đó vẫn còn sản phẩm bên trong.
- Khẳng định việc xóa kho trong tình huống còn tồn kho không nên được cho phép vì sẽ làm sai lệch dữ liệu và phá vỡ tính truy nguyên của hàng hóa.
- Đề xuất hướng xử lý an toàn: chặn xóa khi còn hàng, hoặc yêu cầu kho phải đạt trạng thái không còn tồn kho trước khi được xóa; nếu cần, phải chuyển hoặc điều chuyển hàng hóa trước.
- Cách này giúp bảo toàn tính toàn vẹn của kho và tránh tồn tại sản phẩm treo, số lượng tồn không hợp lệ hoặc dữ liệu không rõ nguồn gốc.

## 5. Demo cho công ty và phản hồi nhận được

- Trình bày luồng kho và tồn kho đã cập nhật cho công ty trong buổi demo on-site.
- Nhận phản hồi tích cực về việc hiển thị Stock Ledger và giao diện kho rõ ràng hơn.
- Công ty cũng nhấn mạnh tầm quan trọng của việc làm cho quy tắc hạn sử dụng sản phẩm có thể cấu hình linh hoạt và đảm bảo thao tác xóa kho được chặn bởi kiểm tra hợp lệ.
- Yêu cầu nâng cấp thêm các điểm này trong vòng lặp tiếp theo để chuẩn bị tốt hơn cho việc đưa vào vận hành thực tế.

## 6. Kết quả và tổng kết

Giao diện Stock Ledger còn thiếu đã được bổ sung, màn hình kho được cải thiện để dễ nhìn hơn, logic backend nhận hàng đã được cập nhật để cho phép người dùng chọn hạn sử dụng tối thiểu thay vì hardcode 2 ngày, và vấn đề xóa kho khi còn hàng đã được xác thực theo hướng xử lý an toàn. Buổi demo on-site đã diễn ra thành công và phản hồi của công ty cho thấy hướng làm hiện tại phù hợp với nhu cầu vận hành, nhưng vẫn cần tinh chỉnh thêm trước khi triển khai rộng hơn.
