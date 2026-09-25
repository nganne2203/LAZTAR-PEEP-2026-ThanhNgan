+++
title = "Ngày 05 - 25/09/2026 (Remote)"
weight = 5
+++

# Báo cáo ngày 05

- **Chế độ làm việc:** Remote
- **Dự án:** Mini-WMS

## A. Công việc thực tế

### 1. Mục tiêu

Hôm nay em tập trung vào công việc tích hợp và review chéo của dự án. Với vai trò phụ trách Domain C, bao gồm Product & Supplier, em cùng các thành viên khác đối chiếu dữ liệu sản phẩm, nhà cung cấp, cùng các domain còn lại để đảm bảo ERD tổng v1 đã được tích hợp đầy đủ và sẵn sàng cho quá trình review.

Mục tiêu chính là kiểm tra điểm nối giữa các domain, chạy kịch bản nghiệp vụ trên giấy và hoàn thiện ERD tổng v1 sau khi có phản hồi từ review.

### 2. Những gì em đã làm

- Tham gia buổi họp tích hợp 60 phút để đi qua các điểm nối được xác định ở mục 6.
- Tham gia các buổi review chéo theo cặp: A↔B, C↔D, D↔E, E↔A.
- Xác nhận các điểm kết nối giữa Domain C với các domain khác, đặc biệt là inventory, receiving, allocation, transfer và adjustment.
- Chạy thử các kịch bản nghiệp vụ trên giấy theo mục 7 của dự án.
- Kiểm tra cách dữ liệu SKU, supplier, UOM và barcode ảnh hưởng đến các quy trình vận hành kho.
- Gộp ERD tổng v1 sau phản hồi review và kiểm tra lần cuối về cấu trúc và tính nhất quán.
- Tích hợp ERD vào tài liệu báo cáo và xác nhận hình ảnh render thành công.
- Ghi lại danh sách lỗi và thay đổi đã xử lý trong quá trình review.

### 3. Đóng góp của Domain C

#### 3.1 Domain C – Product & Supplier

Domain C là nền tảng cho toàn bộ hệ thống WMS. Dữ liệu sản phẩm và nhà cung cấp quyết định mọi quy trình kho có thể vận hành đúng hay không. Nếu SKU, UOM, barcode và dữ liệu supplier không đồng nhất thì các flow nhận hàng, phân bổ, chuyển vị trí, điều chỉnh tồn kho và xuất kho đều không đáng tin cậy.

Các thực thể chính trong Domain C gồm:

- SKU: dữ liệu sản phẩm chính với base UOM, trạng thái, lot control và serial tracking.
- UOM: đơn vị đo lường dùng trong kho.
- SKU-UOM Conversion: quy tắc quy đổi giữa base UOM và UOM vận hành.
- Barcode: mapping barcode riêng cho từng sản phẩm và UOM.
- Supplier: thông tin nhà cung cấp.
- SKU-Supplier: mối quan hệ giữa sản phẩm và nhà cung cấp, bao gồm mã SKU nhà cung cấp và trạng thái preferred supplier.

Quy tắc quan trọng nhất là dữ liệu sản phẩm và nhà cung cấp phải nhất quán trước khi bất kỳ thay đổi tồn kho nào được ghi nhận.

#### 3.2 Điểm nối với các domain khác

Domain C kết nối trực tiếp với chuỗi hoạt động kho:

- Với inventory domain: mỗi SKU phải tồn tại trước khi có thể lưu trữ và kiểm kê.
- Với stock ledger và movement domain: mọi thay đổi số lượng phải được ghi qua movement.
- Với receiving flow: hàng hóa được kiểm tra bằng SKU, UOM, barcode, lot và expiry trước khi nhập kho.
- Với outbound flow: allocation kiểm tra tồn kho dựa trên SKU, lot, số lượng và quy đổi UOM.
- Với transfer flow: thay đổi vị trí lưu trữ gắn với SKU và inventory position.
- Với adjustment flow: chênh lệch kiểm kê được tạo từ dữ liệu inventory và thông tin sản phẩm/nhà cung cấp.

### 4. Review chéo và buổi tích hợp

Buổi họp tích hợp kéo dài 60 phút rất quan trọng vì giúp team phát hiện những điểm chồng chéo và những mismatch ẩn trong thiết kế.

Các vấn đề được review gồm:

- tính nhất quán của khóa ngoại và khóa chính
- quy ước đặt tên giữa các bảng và API
- nơi nào nên thực hiện validation nghiệp vụ
- cách ghi log inventory và stock movements
- cách Domain C ảnh hưởng đến các module vận hành khác

Các buổi review chéo đã làm sáng tỏ các phần khớp nhau như sau:

- A↔B: thống nhất ranh giới luồng nghiệp vụ và quy trình tác nghiệp
- C↔D: dữ liệu sản phẩm và nhà cung cấp được nối với logic tồn kho và movement
- D↔E: vòng đời tồn kho vận hành được liên kết với logic phê duyệt và kiểm soát
- E↔A: luồng governance và control được đồng bộ với quy trình cốt lõi

Nhờ vậy, sự nhập nhằng trong thiết kế đã giảm đáng kể và mô hình tổng thể trở nên đồng nhất hơn.

### 5. Kiểm tra kịch bản nghiệp vụ trên giấy

Em cũng đã kiểm tra các kịch bản nghiệp vụ chính trên giấy để đảm bảo logic trong ERD phù hợp với hoạt động kho thực tế.

Một số kịch bản đã chạy thử:

1. Nhà cung cấp giao hàng và tạo receipt.
2. Hàng hóa được validate theo SKU, UOM, barcode, lot và expiry.
3. Inventory được cập nhật sau put-away và stock ledger ghi nhận movement.
4. Đơn xuất kho kiểm tra khả dụng và reserve inventory.
5. Transfer đổi vị trí mà không làm thay đổi tổng tồn kho.
6. Adjustment được tạo khi kiểm kê lệch và được phê duyệt theo quy trình.

Các kịch bản này cho thấy thiết kế không cho phép thay đổi số lượng tồn kho mà không có movement hợp lệ, điều rất quan trọng trong việc truy nguyên và kiểm soát kho.

### 6. Tích hợp ERD v1 và render hình ảnh

ERD v1 tổng hợp được gộp sau khi review và đã render thành công để chốt lại thiết kế cuối cùng.

![ERD tổng v1](/images/reports/day-05/ERD-V1.webp)

Công việc tích hợp cho thấy sơ đồ cuối cùng có cấu trúc hợp lý và các domain đều được nối với nhau theo luồng dữ liệu, hoạt động kho và lịch sử movement.

### 7. Danh sách lỗi và thay đổi đã xử lý

Trong quá trình review, nhóm đã phát hiện và sửa các vấn đề sau:

- tên trường trùng lặp hoặc không nhất quán giữa các domain
- hướng quan hệ giữa product, inventory và movement chưa rõ ràng
- thiếu hoặc mơ hồ kết nối giữa supplier và product master data
- logic stock ledger và physical stock chưa đồng bộ
- cần chuẩn hóa base UOM và quy đổi ở ranh giới domain
- cần kiểm tra lại rule vị trí và movement trước khi chốt thiết kế cuối cùng

Các thay đổi cuối cùng đã bổ sung mối quan hệ rõ ràng hơn, đồng bộ tên gọi và giúp Domain C kết nối tốt hơn với quy trình kho thực tế.

## B. Tổng kết

### Kiến thức đã học

- Domain C không chỉ là tầng dữ liệu tham chiếu mà còn là nền tảng cho toàn bộ mô hình vận hành kho.
- Review tích hợp là bước cần thiết để phát hiện mismatch ẩn trước khi triển khai.
- ERD tốt phải phản ánh cả cấu trúc dữ liệu lẫn logic nghiệp vụ, không chỉ là các bảng.
- Review chéo theo cặp giúp tìm ra giả định lệch nhau mà một nhóm riêng biệt dễ bỏ qua.

### Vấn đề gặp phải và cách xử lý

- **Ranh giới tích hợp chưa rõ:** em xác nhận lại điểm nối giữa Product & Supplier với vòng đời tồn kho.
- **Tên gọi và quan hệ chưa thống nhất:** em đồng bộ cách đặt tên và làm rõ cardinality.
- **Rủi ro sai logic cập nhật tồn kho:** em củng cố nguyên tắc mọi thay đổi tồn kho đều phải đi qua movement và stock ledger.

## C. Kết luận

Ngày 05 là ngày tích hợp và đồng bộ hóa dự án. Với vai trò phụ trách Domain C, em không chỉ đóng góp vào mô hình product và supplier mà còn đảm bảo tính nhất quán của toàn bộ hệ thống WMS. Các buổi review chéo và thử kịch bản trên giấy giúp team phát hiện mismatch, chỉnh sửa ERD và chuẩn bị một phiên bản mạnh hơn cho giai đoạn triển khai.

Điểm quan trọng nhất là Domain C tạo nền tảng cho toàn bộ quy trình kho. Khi dữ liệu sản phẩm và nhà cung cấp đúng, các luồng nhận hàng, tồn kho, chuyển vị trí, điều chỉnh và xuất kho sẽ ổn định, dễ theo dõi và dễ kiểm tra khi triển khai thực tế.
