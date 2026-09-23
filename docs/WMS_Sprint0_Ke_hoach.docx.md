**SPRINT 0 – KẾ HOẠCH THỰC HIỆN**

Thiết kế nghiệp vụ & Database WMS

&nbsp;

**Thời gian:** T4 23/09/2026 – T2 28/09/2026 (4 ngày làm việc – bỏ qua T7 và CN)

**Hạn nộp:** Hết ngày làm việc T2 28/09/2026

**Nhóm:** 5 trainee

**Mục lục**

[1\. Tổng quan Sprint 0	3](#1.-tổng-quan-sprint-0)

[1.1 Mục tiêu	3](#1.1-mục-tiêu)

[1.2 Deliverables (nộp 1 bộ duy nhất)	3](#1.2-deliverables-\(nộp-1-bộ-duy-nhất\))

[2\. Phân chia domain	3](#2.-phân-chia-domain)

[3\. Quy ước chung (chốt trong ngày 1\)	3](#3.-quy-ước-chung-\(chốt-trong-ngày-1\))

[3.1 Đặt tên	3](#3.1-đặt-tên)

[3.2 Kiểu dữ liệu	4](#3.2-kiểu-dữ-liệu)

[3.3 Cột audit bắt buộc	4](#3.3-cột-audit-bắt-buộc)

[3.4 Xóa dữ liệu	4](#3.4-xóa-dữ-liệu)

[3.5 Công cụ & lưu trữ	4](#3.5-công-cụ-&-lưu-trữ)

[4\. Kế hoạch theo ngày	4](#4.-kế-hoạch-theo-ngày)

[5\. Hướng dẫn chi tiết từng domain	5](#5.-hướng-dẫn-chi-tiết-từng-domain-\(nội-dung-mục-này-chỉ-mang-tính-chất-tham-khảo,-không-cần-thiết-kế-giống-hoàn-toàn.-team-chủ-động-thiết-kế-dựa-trên-business-flow-mà-nhóm-đã-thống-nhất.\))

[5.1 Domain A – Authentication & RBAC	5](#5.1-domain-a-–-authentication-&-rbac)

[5.2 Domain B – Warehouse Structure	5](#5.2-domain-b-–-warehouse-structure)

[5.3 Domain C – Product & Supplier	6](#5.3-domain-c-–-product-&-supplier)

[5.4 Domain D – Inventory Model	6](#5.4-domain-d-–-inventory-model)

[5.5 Domain E – Stock Ledger & Movement	7](#5.5-domain-e-–-stock-ledger-&-movement)

[6\. Điểm nối giữa các domain	8](#6.-điểm-nối-giữa-các-domain)

[7\. Kịch bản kiểm thử thiết kế trên giấy	8](#7.-kịch-bản-kiểm-thử-thiết-kế-trên-giấy)

[8\. Definition of Done	8](#8.-definition-of-done)

[9\. Rủi ro và cách xử lý	9](#9.-rủi-ro-và-cách-xử-lý)

[10\. Cấu trúc thư mục trên Google Drive	9](#10.-cấu-trúc-thư-mục-trên-google-drive)

[Phụ lục	9](#phụ-lục)

[A. Mẫu Data Dictionary	9](#a.-mẫu-data-dictionary)

[B. Mẫu Business Rule	9](#b.-mẫu-business-rule)

[C. Khung PlantUML ERD	9](#c.-khung-plantuml-erd)

&nbsp;

*(Nếu mục lục trống: trong Word nhấn chuột phải → Update Field; trong Google Docs dùng Insert → Table of contents.)*

# **1\. Tổng quan Sprint 0** {#1.-tổng-quan-sprint-0}

## **1.1 Mục tiêu** {#1.1-mục-tiêu}

Trong 4 ngày, nhóm 5 trainee tự chia việc theo 5 domain và cùng nộp một bộ tài liệu thiết kế thống nhất cho hệ thống quản lý kho (WMS). Trọng tâm không chỉ là mỗi người làm xong phần của mình, mà là các phần ghép lại được với nhau: cùng quy ước đặt tên, khóa ngoại khớp nhau, và luồng nghiệp vụ chạy xuyên suốt qua cả 5 domain.

## **1.2 Deliverables (nộp 1 bộ duy nhất)** {#1.2-deliverables-(nộp-1-bộ-duy-nhất)}

| \# | Deliverable | Định dạng |
| :---- | :---- | :---- |
| 1 | Business Flow (Inbound, Outbound, Transfer, Adjustment) | PlantUML (.puml) hoặc Draw.io \+ ảnh PNG |
| 2 | ERD v1 toàn hệ thống | PlantUML (.puml) \+ ảnh PNG |
| 3 | Data Dictionary | Google Sheet / Excel (1 tab mỗi domain) |
| 4 | Danh sách Business Rules | Google Sheet / Doc, mã BR-xx-nn |

&nbsp;

# **2\. Phân chia domain** {#2.-phân-chia-domain}

Đề bài không chỉ định ai làm gì. Nhóm chốt điền tên vào bảng dưới. Gợi ý cách chọn: ai có kinh nghiệm SQL/transaction nhất nên nhận D hoặc E (hai domain gắn chặt nhau và khó nhất); người nhận A nên kiêm chủ trì Business Flow vì phải hiểu ai làm bước nào.

| Domain | Phạm vi | Bảng chính (đề xuất) | Phụ thuộc vào | Phụ trách |
| :---- | :---- | :---- | :---- | :---- |
| A | Authentication & RBAC | users, roles, permissions, role\_permissions, user\_roles, user\_warehouses | B (phân quyền theo kho) | \_\_\_\_\_\_\_\_ |
| B | Warehouse Structure | warehouses, locations (Zone → Aisle → Rack → Bin) | — | \_\_\_\_\_\_\_\_ |
| C | Product & Supplier | skus, suppliers, sku\_suppliers, uoms, sku\_uom\_conversions, sku\_barcodes | — | \_\_\_\_\_\_\_\_ |
| D | Inventory Model | inventory (on\_hand, reserved, available) | B, C | \_\_\_\_\_\_\_\_ |
| E | Stock Ledger & Movement | stock\_ledger, movement\_types, reference\_types | A, B, C, D | \_\_\_\_\_\_\_\_ |

&nbsp;

**Thứ tự phụ thuộc:** B và C là "gốc", cần chốt khóa chính sớm nhất để D và E tham chiếu. A độc lập nhưng cần biết danh sách hành động nghiệp vụ để định nghĩa permission.

# **3\. Quy ước chung (chốt trong ngày 1\)** {#3.-quy-ước-chung-(chốt-trong-ngày-1)}

Đây là phần quan trọng nhất để 5 phần ghép lại được. Nhóm có thể sửa, nhưng phải chốt trước khi bắt tay vẽ ERD.

## **3.1 Đặt tên** {#3.1-đặt-tên}

* Tên bảng: snake\_case, số nhiều, tiếng Anh (users, stock\_ledger là ngoại lệ vì là danh từ không đếm được).

* Tên cột: snake\_case; khóa chính là id; khóa ngoại là \<bảng số ít\>\_id (ví dụ warehouse\_id, sku\_id).

* Cột trạng thái/loại dùng mã chữ in hoa: ACTIVE, INACTIVE, RECEIPT, SHIP...

* Cột boolean bắt đầu bằng is\_ / has\_ (is\_active, is\_pickable).

&nbsp;

&nbsp;

## **3.2 Kiểu dữ liệu** {#3.2-kiểu-dữ-liệu}

* Khóa chính: BIGINT tự tăng (hoặc UUID — chọn một, áp dụng toàn hệ thống).

* Số lượng tồn: DECIMAL(18,4) để hỗ trợ đơn vị lẻ (kg, mét); không dùng FLOAT.

* Thời gian: TIMESTAMP lưu theo UTC; hiển thị theo múi giờ người dùng.

* Mã nghiệp vụ (sku\_code, location\_code, warehouse\_code): VARCHAR, UNIQUE, không cho sửa sau khi đã phát sinh giao dịch.

## **3.3 Cột audit bắt buộc** {#3.3-cột-audit-bắt-buộc}

Mọi bảng master (trừ stock\_ledger) có: created\_at, created\_by, updated\_at, updated\_by. Bảng stock\_ledger chỉ có created\_at, created\_by vì không bao giờ được sửa.

## **3.4 Xóa dữ liệu** {#3.4-xóa-dữ-liệu}

Không xóa cứng dữ liệu master đã phát sinh giao dịch. Dùng is\_active \= false hoặc cột status. Xóa cứng chỉ cho phép với bản ghi chưa từng được tham chiếu.

## **3.5 Công cụ & lưu trữ** {#3.5-công-cụ-&-lưu-trữ}

* ERD: PlantUML, mỗi domain một file .puml, có một file tổng include tất cả.

* Business Flow: PlantUML activity diagram (swimlane theo vai trò) hoặc Draw.io.

* Lưu bản nguồn trên Git (repo chung) và bản xuất (PNG/PDF) trên Google Drive.

# **4\. Kế hoạch theo ngày** {#4.-kế-hoạch-theo-ngày}

| Ngày | Mục tiêu | Công việc chính | Đầu ra cuối ngày |
| :---- | :---- | :---- | :---- |
| T4 23/09 Quy ước | Cả nhóm hiểu chung một bức tranh WMS | Chọn domain, chọn chủ trì deliverable Chốt quy ước (mục 3\) Cùng vẽ nháp Business Flow tổng: Inbound → Putaway → Pick → Ship; Transfer; Adjustment/Cycle count Mỗi người liệt kê bảng \+ câu hỏi mở của domain mình | Bảng phân công đã điền tên Quy ước v1 Business Flow nháp Danh sách bảng từng domain |
| T5 24/09 Thiết kế domain | Mỗi domain có bản nháp đầy đủ | Vẽ ERD domain (.puml) Viết Data Dictionary domain Viết Business Rules domain (≥ 5 rule/domain) B và C chốt khóa chính trước 15h để D, E dùng Stand-up 15 phút cuối ngày | 5 ERD domain nháp Data Dictionary nháp Business Rules nháp |
| T6 25/09 Tích hợp & review chéo | Các phần khớp nhau | Họp tích hợp 60 phút: đi qua mục 6 (điểm nối) Review chéo theo cặp: A↔B, C↔D, D↔E, E↔A Chạy thử kịch bản nghiệp vụ trên giấy (mục 7\) Gộp ERD tổng v1 | ERD tổng v1 render được Danh sách lỗi/thay đổi đã xử lý |
| T2 28/09 Tổng duyệt & nộp | Nộp tài liệu | Nộp lên Drive (Tới đây công ty sẽ gửi link driver để nộp)&nbsp; | Bộ tài liệu cuối trên Drive&nbsp; |

&nbsp;

**Nhịp làm việc hằng ngày:** stand-up 15 phút đầu ngày (hôm qua làm gì, hôm nay làm gì, đang vướng gì) và sync 15 phút cuối ngày để cập nhật thay đổi ảnh hưởng domain khác.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

# **5\. Hướng dẫn chi tiết từng domain (Nội dung mục này chỉ mang tính chất tham khảo, không cần thiết kế giống hoàn toàn. Team chủ động thiết kế dựa trên business flow mà nhóm đã thống nhất.)** {#5.-hướng-dẫn-chi-tiết-từng-domain-(nội-dung-mục-này-chỉ-mang-tính-chất-tham-khảo,-không-cần-thiết-kế-giống-hoàn-toàn.-team-chủ-động-thiết-kế-dựa-trên-business-flow-mà-nhóm-đã-thống-nhất.)}

Phần này là gợi ý khởi điểm để không ai bắt đầu từ trang trắng. Người phụ trách (Nhóm trưởng) có quyền thay đổi, nhưng cần ghi lý do vào tài liệu.

## **5.1 Domain A – Authentication & RBAC** {#5.1-domain-a-–-authentication-&-rbac}

### **Bảng đề xuất**

| Bảng | Cột chính | Ghi chú |
| :---- | :---- | :---- |
| users | id, username, email, password\_hash, full\_name, status, last\_login\_at | status: ACTIVE, LOCKED, INACTIVE |
| roles | id, code, name, description | Ví dụ: ADMIN, WH\_MANAGER, SUPERVISOR, RECEIVER, PICKER, INV\_CONTROLLER, VIEWER |
| permissions | id, code, module, action | Ví dụ: INBOUND.RECEIVE, INVENTORY.ADJUST, LEDGER.VIEW |
| role\_permissions | role\_id, permission\_id | N–N |
| user\_roles | user\_id, role\_id, warehouse\_id | Gán vai trò theo từng kho (warehouse\_id null \= toàn hệ thống) |

&nbsp;

### **Câu hỏi cần trả lời**

* Một người có thể làm nhiều vai trò ở nhiều kho khác nhau không?

* Ai được phép điều chỉnh tồn kho (adjustment)? Có cần duyệt 2 cấp khi điều chỉnh số lượng lớn?

* Tách quyền "xem" và "thao tác" đến mức nào?

### **Business Rules gợi ý**

* Người dùng chỉ thao tác trên kho mà họ được gán vai trò.

* Người tạo phiếu điều chỉnh không được tự duyệt phiếu đó (tách biệt nhiệm vụ).

* Khóa tài khoản sau N lần đăng nhập sai liên tiếp.

## **5.2 Domain B – Warehouse Structure** {#5.2-domain-b-–-warehouse-structure}

### **Hai phương án mô hình vị trí**

| Phương án | Mô tả | Ưu điểm | Nhược điểm |
| :---- | :---- | :---- | :---- |
| 1\. Bảng riêng từng cấp | zones, aisles, racks, bins nối khóa ngoại lần lượt | Rõ ràng, dễ ràng buộc | Cứng; kho nào không có Aisle thì khó |
| 2\. Một bảng locations tự tham chiếu | locations(id, parent\_id, location\_type, code, ...) | Linh hoạt, số cấp tùy kho | Truy vấn cây phức tạp hơn, cần ràng buộc thứ tự cấp |

&nbsp;

Khuyến nghị: phương án 2, và quy định inventory chỉ được gắn vào location có location\_type \= BIN. Cân nhắc thêm cột path (ví dụ WH01/Z-A/A01/R03/B05) để truy vấn nhanh.

### **Bảng đề xuất**

| Bảng | Cột chính | Ghi chú |
| :---- | :---- | :---- |
| warehouses | id, code, name, address, status |  |
| locations | id, warehouse\_id, parent\_id, location\_type, code, full\_path, purpose, max\_weight, max\_volume, is\_pickable, is\_active | location\_type: ZONE, AISLE, RACK, BIN purpose: RECEIVING, STORAGE, PICKING, STAGING, QC, DAMAGED |

&nbsp;

### 

### **Business Rules gợi ý**

* location code là duy nhất trong một kho.

* Cấp cha phải đúng thứ tự: BIN thuộc RACK, RACK thuộc AISLE, AISLE thuộc ZONE.

* Không được vô hiệu hóa location đang còn tồn kho.

* Tồn ở location có purpose \= DAMAGED hoặc QC không được tính vào available để bán.

## **5.3 Domain C – Product & Supplier** {#5.3-domain-c-–-product-&-supplier}

### **Bảng đề xuất**

| Bảng | Cột chính | Ghi chú |
| :---- | :---- | :---- |
| skus | id, sku\_code, name, base\_uom\_id, category, weight, volume, status, is\_lot\_tracked, is\_serial\_tracked | status: DRAFT, ACTIVE, INACTIVE, DISCONTINUED |
| uoms | id, code, name | EA, BOX, CARTON, KG... |
| sku\_uom\_conversions | sku\_id, uom\_id, factor\_to\_base | 1 BOX \= 12 EA |
| sku\_barcodes | id, sku\_id, uom\_id, barcode, barcode\_type, is\_primary | Một SKU nhiều barcode, mỗi UoM một barcode |
| suppliers | id, code, name, tax\_code, contact, status |  |
| sku\_suppliers | sku\_id, supplier\_id, supplier\_sku\_code, is\_preferred | N–N |

&nbsp;

### **Business Rules gợi ý**

* barcode là duy nhất trên toàn hệ thống.

* Mọi số lượng lưu trong inventory và stock\_ledger đều quy đổi về base UoM.

* Chỉ SKU ở trạng thái ACTIVE mới được nhập kho mới; DISCONTINUED vẫn được xuất hết tồn.

* Không được đổi base\_uom của SKU đã phát sinh tồn kho.

## **5.4 Domain D – Inventory Model** {#5.4-domain-d-–-inventory-model}

### **Công thức cốt lõi**

qty\_on\_hand    \= tồn vật lý đang nằm tại location (tổng qty\_change trong stock\_ledger)

qty\_reserved   \= số lượng đã giữ chỗ cho đơn xuất nhưng chưa lấy khỏi kệ

qty\_available  \= qty\_on\_hand \- qty\_reserved

&nbsp;

Ràng buộc: qty\_on\_hand \>= 0, qty\_reserved \>= 0, qty\_reserved \<= qty\_on\_hand

&nbsp;

### **Bảng đề xuất**

| Cột | Kiểu | Ghi chú |
| :---- | :---- | :---- |
| id | BIGINT PK |  |
| warehouse\_id | FK → warehouses | Lưu thừa để truy vấn nhanh theo kho |
| location\_id | FK → locations | Chỉ BIN |
| sku\_id | FK → skus |  |
| lot\_no, expiry\_date | VARCHAR, DATE (tùy chọn) | Nếu SKU quản lý theo lô |
| qty\_on\_hand, qty\_reserved | DECIMAL(18,4) | Theo base UoM |
| qty\_available | Cột tính toán (generated) hoặc tính khi truy vấn | Không cho ghi trực tiếp |
| version | INT | Optimistic locking chống ghi đè đồng thời |
| updated\_at | TIMESTAMP |  |

&nbsp;

&nbsp;

Khóa duy nhất: (location\_id, sku\_id, lot\_no).

### **Câu hỏi cần trả lời**

* Giữ chỗ ở cấp kho (warehouse) hay cấp location? Cấp kho đơn giản hơn nhưng khi pick phải chọn location sau.

* Hàng đang trên đường chuyển kho (in-transit) tính ở đâu?

* Có cho phép tồn âm tạm thời không? (Khuyến nghị: không.)

## **5.5 Domain E – Stock Ledger & Movement** {#5.5-domain-e-–-stock-ledger-&-movement}

### **Bảng đề xuất**

| Cột | Ghi chú |
| :---- | :---- |
| id | BIGINT PK, tăng dần |
| warehouse\_id, location\_id, sku\_id, lot\_no | Khớp với khóa của inventory |
| movement\_type | Loại biến động (bảng dưới) |
| qty\_change | Có dấu: \+ nhập, – xuất; theo base UoM |
| qty\_before, qty\_after | Tồn on\_hand trước/sau tại location đó (giúp đối soát) |
| reference\_type, reference\_id | Chứng từ gốc: RECEIPT, SHIPMENT, TRANSFER, ADJUSTMENT, CYCLE\_COUNT |
| reversal\_of\_id | Nếu là bút toán đảo, trỏ tới dòng bị đảo |
| note, created\_at, created\_by | Không có updated\_\* |

&nbsp;

### **Movement types đề xuất**

| Mã | Dấu qty | Ý nghĩa |
| :---- | :---- | :---- |
| RECEIPT | \+ | Nhập hàng từ nhà cung cấp vào location nhận hàng |
| PUTAWAY\_OUT / PUTAWAY\_IN | – / \+ | Chuyển từ khu nhận hàng lên kệ lưu trữ |
| PICK | – | Lấy hàng khỏi kệ (đồng thời giảm reserved) |
| SHIP | – | Xuất khỏi kho từ khu staging |
| TRANSFER\_OUT / TRANSFER\_IN | – / \+ | Chuyển giữa location hoặc giữa kho |
| ADJUST\_IN / ADJUST\_OUT | \+ / – | Điều chỉnh sau kiểm kê, hư hỏng, mất mát |
| REVERSAL | đảo dấu | Hủy một bút toán sai |

&nbsp;

Lưu ý: giữ chỗ (reserve/release) không thay đổi tồn vật lý nên không ghi vào stock\_ledger. Nếu cần lịch sử giữ chỗ, dùng bảng riêng (ví dụ inventory\_reservations) — hai domain D và E phải thống nhất điểm này.

### **Quy tắc append-only**

* Chỉ INSERT; cấm UPDATE và DELETE (thu hồi quyền ở mức DB hoặc dùng trigger chặn).

* Sửa sai bằng cách ghi bút toán đảo (REVERSAL) rồi ghi bút toán đúng.

* Mỗi lần ghi ledger và cập nhật inventory phải nằm trong cùng một transaction.

* Bất biến đối soát: SUM(qty\_change) theo (location, sku, lot) \= inventory.qty\_on\_hand.

# 

# 

# **6\. Điểm nối giữa các domain** {#6.-điểm-nối-giữa-các-domain}

Đây là checklist cho buổi họp tích hợp ngày T6 25/09. Mỗi dòng cần cả hai bên xác nhận.

| Điểm nối | Domain | Câu hỏi phải thống nhất |
| :---- | :---- | :---- |
| Phân quyền theo kho | A ↔ B | user\_roles.warehouse\_id trỏ đúng bảng warehouses? Quyền có xuống cấp zone không? |
| Người thực hiện giao dịch | A ↔ E | stock\_ledger.created\_by là users.id; ai được xem ledger? |
| Tồn gắn với vị trí | B ↔ D | Chỉ BIN có tồn? Location QC/DAMAGED có tính vào available? |
| Tồn gắn với SKU & UoM | C ↔ D | Lưu theo base UoM; lot/serial tracking lấy cờ từ skus |
| Inventory ↔ Ledger | D ↔ E | Cùng khóa (location, sku, lot); cập nhật trong cùng transaction; reserve có ghi ledger không |
| Chứng từ tham chiếu | E ↔ (tương lai) | reference\_type liệt kê những loại chứng từ nào dù Sprint 0 chưa thiết kế bảng chứng từ |
| Trạng thái vô hiệu hóa | B, C ↔ D | Không deactivate location/SKU còn tồn |

&nbsp;

# **7\. Kịch bản kiểm thử thiết kế trên giấy** {#7.-kịch-bản-kiểm-thử-thiết-kế-trên-giấy}

Ngày T6 25/09, cả nhóm đi qua từng kịch bản, ghi ra bảng nào được INSERT/UPDATE và giá trị thay đổi ra sao. Nếu kịch bản nào không đi hết được, thiết kế đang thiếu.

| \# | Kịch bản | Kỳ vọng |
| :---- | :---- | :---- |
| 1 | Nhập 10 BOX (1 BOX \= 12 EA) SKU-001 từ nhà cung cấp vào RECV-01 | Ledger \+120 EA RECEIPT; inventory RECV-01 on\_hand \= 120 |
| 2 | Putaway 120 EA từ RECV-01 lên BIN A01-R03-B05 | 2 dòng ledger (–120, \+120); on\_hand tổng không đổi |
| 3 | Đơn xuất 30 EA → giữ chỗ | reserved \= 30, available \= 90; ledger không đổi |
| 4 | Pick 30 EA và ship | on\_hand \= 90, reserved \= 0; ledger ghi PICK/SHIP |
| 5 | Kiểm kê thấy thiếu 2 EA | ADJUST\_OUT –2 bởi người có quyền; cần duyệt nếu có rule |
| 6 | Phát hiện bút toán ở bước 1 nhập sai SKU | REVERSAL –120 rồi RECEIPT đúng SKU; không UPDATE dòng cũ |
| 7 | Picker thử điều chỉnh tồn ở kho không được gán | Bị từ chối theo RBAC |
| 8 | Hai người cùng giữ chỗ 90 EA cuối cùng đồng thời | Chỉ một người thành công (version/lock) |

&nbsp;

&nbsp;

Chuẩn bị sẵn câu trả lời cho các câu hỏi dễ bị hỏi: vì sao chọn một bảng locations; vì sao reserve không ghi ledger (hoặc có); làm sao đảm bảo inventory khớp ledger; xử lý đồng thời thế nào; đơn vị tính quy đổi ra sao.

# **8\. Definition of Done** {#8.-definition-of-done}

* Business Flow bao phủ ít nhất Inbound, Outbound, Transfer, Adjustment và có swimlane theo vai trò.

* ERD tổng render được bằng PlantUML, không có bảng "mồ côi" không nối với ai.

* Mọi khóa ngoại trong ERD có mặt trong Data Dictionary với đúng kiểu dữ liệu.

* Data Dictionary đủ các cột: bảng, cột, kiểu, null, mặc định, khóa, mô tả, ví dụ.

* Mỗi domain có ít nhất 5 Business Rule, có mã BR và nguồn/lý do.

* Cả 8 kịch bản ở mục 7 đi qua được trên thiết kế.

* Quy ước ở mục 3 được áp dụng nhất quán (đã có người review riêng việc này).

* Toàn bộ file đã đưa lên Drive đúng cấu trúc thư mục ở mục 10\.

# **9\. Rủi ro và cách xử lý** {#9.-rủi-ro-và-cách-xử-lý}

| Rủi ro | Dấu hiệu | Cách xử lý |
| :---- | :---- | :---- |
| 5 phần không ghép được | Tên cột, kiểu khóa khác nhau giữa domain | Chốt quy ước ngày 1; B, C chốt khóa chính trước 15h ngày 2 |
| D và E hiểu khác nhau về tồn | Tranh luận reserve có vào ledger không | Hai người D, E ngồi chung ngay ngày 2, ghi quyết định vào tài liệu |
| Lan man phạm vi | Thiết kế luôn đơn hàng, vận chuyển, báo cáo | Chỉ ghi các chứng từ đó là reference\_type; để thiết kế chi tiết cho sprint sau |
| Dồn việc vào ngày cuối | Ngày 4 chưa có ERD tổng | Mốc cứng: ERD tổng v1 cuối ngày 3 |
| Một người vắng/chậm | Không cập nhật ở stand-up | Cặp review chéo (mục 4\) là người dự phòng |

&nbsp;

# **10\. Cấu trúc thư mục trên Google Drive** {#10.-cấu-trúc-thư-mục-trên-google-drive}

WMS\_Sprint0/

├── 00\_Plan/                 (tài liệu kế hoạch này, biên bản họp)

├── 01\_Business\_Flow/        (.puml / .drawio \+ PNG)

├── 02\_ERD/                  (erd\_all.puml, erd\_domain\_A..E.puml, erd\_v1.png)

├── 03\_Data\_Dictionary/      (WMS\_Data\_Dictionary – 1 tab mỗi domain)

├── 04\_Business\_Rules/       (WMS\_Business\_Rules)

└── 99\_Working/              (nháp từng người, không nộp)

&nbsp;

# **Phụ lục** {#phụ-lục}

## **A. Mẫu Data Dictionary** {#a.-mẫu-data-dictionary}

| Bảng | Cột | Kiểu | Null | Mặc định | Khóa | Mô tả | Ví dụ |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| inventory | qty\_on\_hand | DECIMAL(18,4) | N | 0 |  | Tồn vật lý theo base UoM | 120 |
| inventory | location\_id | BIGINT | N |  | FK→locations.id | BIN chứa hàng | 1024 |

## 

## **B. Mẫu Business Rule** {#b.-mẫu-business-rule}

| Mã | Domain | Nội dung | Áp dụng tại | Nguồn/Lý do |
| :---- | :---- | :---- | :---- | :---- |
| BR-D-01 | Inventory | qty\_reserved không được lớn hơn qty\_on\_hand | Khi giữ chỗ | Tránh hứa bán hàng không có |
| BR-E-01 | Ledger | stock\_ledger chỉ được INSERT, sửa sai bằng REVERSAL | Mọi giao dịch kho | Truy vết, kiểm toán |

&nbsp;

## 

## 

## 

&nbsp;

&nbsp;

## **C. Khung PlantUML ERD** {#c.-khung-plantuml-erd}

@startuml erd\_all

hide circle

skinparam linetype ortho

&nbsp;

entity warehouses {

&nbsp;&nbsp;\* id : BIGINT \<\<PK\>\>

&nbsp;&nbsp;\--

&nbsp;&nbsp;\* code : VARCHAR(20) \<\<UK\>\>

&nbsp;&nbsp;\* name : VARCHAR(100)

}

&nbsp;

entity locations {

&nbsp;&nbsp;\* id : BIGINT \<\<PK\>\>

&nbsp;&nbsp;\--

&nbsp;&nbsp;\* warehouse\_id : BIGINT \<\<FK\>\>

&nbsp;&nbsp;parent\_id : BIGINT \<\<FK\>\>

&nbsp;&nbsp;\* location\_type : VARCHAR(10)

&nbsp;&nbsp;\* code : VARCHAR(50)

}

&nbsp;

entity inventory {

&nbsp;&nbsp;\* id : BIGINT \<\<PK\>\>

&nbsp;&nbsp;\--

&nbsp;&nbsp;\* location\_id : BIGINT \<\<FK\>\>

&nbsp;&nbsp;\* sku\_id : BIGINT \<\<FK\>\>

&nbsp;&nbsp;\* qty\_on\_hand : DECIMAL(18,4)

&nbsp;&nbsp;\* qty\_reserved : DECIMAL(18,4)

}

&nbsp;

warehouses ||--o{ locations

locations  |o--o{ locations : parent

locations  ||--o{ inventory

@enduml

&nbsp;