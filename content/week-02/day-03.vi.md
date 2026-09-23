+++
title = "Ngày 03 - 23/09/2026 (Remote)"
weight = 3
+++

# Báo cáo ngày 03

## 1. Mục tiêu học tập hôm nay

Hôm nay em tập trung hoàn thiện phần thiết kế nghiệp vụ cho domain C – Product & Supplier và đồng thời chốt lại business flow chính của dự án theo tài liệu Mini-WMS Business Flow. Mục tiêu chính là hiểu rõ cách SKU, nhà cung cấp, quy đổi đơn vị và thông tin lô hàng tương tác với các flow nhập kho, xuất kho, chuyển vị trí và điều chỉnh tồn kho.

Ngoài ra, em cũng chọn vai trò trong dự án theo hướng Frontend và xác định rõ phạm vi công việc, UI cần thiết và những dữ liệu mà frontend cần lấy từ backend để hỗ trợ nghiệp vụ kho.

## 2. Những gì em đã làm

- Chọn domain C: Product & Supplier làm trọng tâm thiết kế hôm nay.
- Đọc lại tài liệu business flow của Mini-WMS và đối chiếu với các luồng nhập, xuất, transfer và adjustment.
- Xác định phạm vi dữ liệu của SKU, UOM, barcode, nhà cung cấp và mối quan hệ với inventory.
- Vẽ ERD mô phỏng domain C và các entity liên quan đến stock ledger và warehouse location.
- Chốt lại business flow tổng thể theo hướng chuẩn của dự án:
  - Inbound: nhận hàng → kiểm tra dữ liệu → putaway → lưu kho
  - Outbound: tạo đơn → allocation → pick → pack → ship
  - Transfer: chuyển giữa location hoặc zone
  - Adjustment: kiểm kê → duyệt → cập nhật tồn
- Lựa chọn vai trò Frontend trong team và xác định nhiệm vụ chính của vai trò này trong dự án Mini-WMS.

## 3. Kiến thức đã học

### 3.1 Domain C – Product & Supplier

Domain C tập trung vào dữ liệu nền tảng mà mọi luồng kho đều phụ thuộc vào. Nếu SKU, UOM, barcode hoặc supplier không chính xác, toàn bộ quy trình nhận hàng, tồn kho, phân bổ và giao hàng sẽ bị sai.

Các entity chính trong domain C gồm:

- SKU: mã sản phẩm, tên, trạng thái, base UOM, quản lý lot/serial.
- UOM: đơn vị tính, ví dụ EA, BOX, CARTON, KG.
- SKU-UOM Conversion: quy đổi giữa các đơn vị tính về base UOM.
- SKU Barcodes: mã vạch tương ứng với sản phẩm và UOM.
- Supplier: thông tin nhà cung cấp.
- SKU Supplier: quan hệ SKU – Supplier, kèm supplier SKU code và nhà cung cấp ưu tiên.

Điểm quan trọng là mọi số lượng trong inventory và stock ledger phải được lưu theo base UOM để tránh sai lệch khi chuyển đổi giữa các đơn vị tính.

### 3.2 Business Flow chốt theo document

Theo tài liệu `MINI-WMS — BUSINESS FLOW`, dự án được xây dựng quanh 4 flow cốt lõi:

1. Inbound

   - nhân viên kho nhận hàng từ nhà cung cấp
   - hệ thống kiểm tra UOM, lot, hạn dùng
   - tăng tồn tạm tại receiving
   - putaway lên BIN phù hợp
   - chuyển tồn từ receiving sang storage location
2. Outbound

   - quản lý kho tạo đơn hàng
   - hệ thống tìm tồn khả dụng theo FEFO
   - đồng bộ allocation cho đơn
   - nhân viên kho pick theo BIN/lot đã được giữ chỗ
   - pack và ship
   - trừ tồn và ghi lịch sử giao hàng
3. Transfer

   - chuyển hàng giữa các vị trí trong cùng kho
   - kiểm tra source và destination hợp lệ
   - không làm thay đổi tổng tồn kho
   - giữ nguyên tính nguyên vẹn của dữ liệu vị trí
4. Adjustment

   - kiểm kê thực tế và so sánh với hệ thống
   - nếu chênh lệch thì tạo yêu cầu điều chỉnh
   - quản lý kho duyệt hoặc bác bỏ
   - chỉ khi được duyệt mới cập nhật tồn kho và ghi ledger

Điều cốt lõi là: mọi thay đổi tồn kho đều đi qua stock ledger, không sửa trực tiếp bảng tồn kho. Đây là nguyên tắc nền tảng của hệ thống WMS.

### 3.3 Business Rules quan trọng thuộc Domain C

Những quy tắc quan trọng mà em chốt được trong domain C:

- Mỗi SKU phải có base UOM duy nhất.
- Barcode phải là duy nhất trên toàn hệ thống.
- Chỉ SKU ở trạng thái ACTIVE mới được phép nhập kho mới.
- Không được đổi base UOM của SKU nếu SKU đã có tồn kho.
- Một SKU có thể có nhiều barcode theo từng UOM.
- Một nhà cung cấp có thể cung cấp nhiều SKU, và một SKU có thể có nhiều nhà cung cấp.
- SKU được quản lý theo lot/expiry nếu thuộc loại hàng có yêu cầu truy xuất.

Các quy tắc này không chỉ ảnh hưởng đến dữ liệu master, mà còn quyết định logic kiểm tra nghiệp vụ ở frontend và backend.

## 4. ERD mô phỏng cho Domain C và luồng kho

ERD trên mô phỏng cách dữ liệu chuỗi kho hoạt động: SKU, nhà cung cấp và quy đổi đơn vị là “dữ liệu nền”, còn inventory và stock ledger là “dữ liệu vận hành”. Hai lớp này phải được kết nối chặt chẽ để tránh tồn kho sai.

## 5. Chốt business flow của dự án

### 5.1 Flow nhập kho (Inbound)

- Supplier giao hàng theo PO/receipt
- hệ thống kiểm tra SKU, UOM, lot, hạn dùng
- nhận hàng vào area receiving
- đặt hàng vào đúng location bằng putaway
- ghi nhận stock ledger với movement type RECEIPT/PUTAWAY

### 5.2 Flow xuất kho (Outbound)

- tạo đơn hàng cần giao
- hệ thống kiểm tra tồn khả dụng và thực hiện allocation theo FEFO
- nhân viên kho pick hàng từ bin đã giữ chỗ
- đóng gói và xác nhận shipping
- trừ tồn kho và ghi lịch sử giao hàng

### 5.3 Flow chuyển vị trí (Transfer)

- chuyển hàng từ source bin sang destination bin
- tổng tồn trong kho không đổi
- chỉ thay đổi vị trí phân bố hàng hóa

### 5.4 Flow điều chỉnh tồn kho (Adjustment)

- kiểm kê thực tế và so sánh với dữ liệu hệ thống
- nhân viên kho tạo request điều chỉnh
- quản lý kho duyệt hoặc từ chối
- nếu được duyệt, ghi bút toán điều chỉnh và cập nhật inventory

## 6. Vai trò em chọn trong dự án: Frontend

Với vai trò Frontend, em sẽ tập trung vào việc xây dựng trải nghiệm người dùng cho các flow kho, đồng thời đảm bảo tính trực quan, rõ ràng và giảm sai sót thao tác của nhân viên kho.

### 6.1 Vai trò cụ thể

Em chọn Frontend Developer / Frontend Engineer, tập trung vào các màn hình sau:

- Dashboard kho và tổng quan tồn kho
- Quản lý SKU, danh mục sản phẩm, barcode
- Quản lý nhà cung cấp và sản phẩm theo nhà cung cấp
- Màn hình nhận hàng và putaway
- Màn hình công việc soạn hàng / picking / packing
- Màn hình kiểm kê và duyệt điều chỉnh tồn
- UI xác thực quyền truy cập theo role

### 6.2 Nhiệm vụ chính của frontend trong dự án

- Hiển thị dữ liệu master theo SKU, UOM, supplier, location.
- Xây dựng form nhập kho với validation đầy đủ: SKU, số lượng, lot, hạn dùng, kho nhận.
- Hiển thị luồng putaway và transfer một cách trực quan.
- Cho phép quản lý kho kiểm tra inventory và allocation trước khi giao hàng.
- Hiển thị lịch sử stock ledger ở cấp đơn giản và dễ hiểu.
- Tạo các màn hình approve/reject adjustment với workflow rõ ràng.
- Bảo đảm UI/UX đúng với quy trình thực tế của kho, tránh tình trạng thao tác sai do giao diện mơ hồ.

### 6.3 Về kỹ năng cần có

Đối với vai trò Frontend trong dự án này, em cần tập trung vào:

- React + TypeScript + Next.js
- Form validation và business rule display
- quản lý state cho workflow kho
- phân quyền UI theo role
- gọi API chuẩn REST/JSON
- tích hợp bảng dữ liệu, filter, search và phân trang
- xử lý trạng thái loading/error cho các thao tác kho quan trọng

### 6.4 Lý do Frontend là vai trò phù hợp với em

Vì project WMS là hệ thống làm việc rất nhiều với nghiệp vụ thực tế, nên frontend không chỉ là “làm đẹp”. Frontend ở đây đóng vai trò trung gian giữa người dùng và hệ thống nghiệp vụ. Nếu giao diện tốt, nhân viên kho sẽ thao tác đúng, giảm sai số, và dễ kiểm soát quyết định trong vận hành hàng ngày.

## 7. Kết luận

Ngày 03 là ngày em chốt lại kiến trúc dữ liệu và business flow của dự án theo hướng thực tế hơn. Domain C – Product & Supplier là nền móng cho toàn bộ hệ thống kho vì mọi thao tác từ nhập, xuất, transfer, đến điều chỉnh đều dựa trên SKU, UOM, supplier và barcode.

Qua việc đối chiếu tài liệu business flow và chốt ERD mô phỏng, em nhận ra rằng WMS không chỉ là một ứng dụng CRUD, mà là một hệ thống có rất nhiều ràng buộc từ nghiệp vụ, dữ liệu và quyền truy cập. Đây cũng là lý do frontend trong dự án không thể chỉ làm giao diện đẹp, mà phải hỗ trợ đúng quy trình vận hành, bảo đảm người dùng thao tác có hướng dẫn rõ ràng và dữ liệu hiển thị phản ánh thực tế kho.

## 8. Kỳ vọng cho các ngày tiếp theo

- Hoàn thiện mô hình domain C chi tiết hơn với data dictionary và business rules.
- Liên kết Domain C với Domain D (Inventory) và Domain E (Stock Ledger).
- Tích hợp ERD với các flow nghiệp vụ thực tế của inbound/outbound.
- Bắt đầu chuẩn bị mockup UI cho các màn hình chính của frontend.
- Đồng bộ với team để thống nhất cách đặt tên bảng, khóa và luồng dữ liệu.
