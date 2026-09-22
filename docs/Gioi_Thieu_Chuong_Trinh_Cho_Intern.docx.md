**CHÀO MỪNG BẠN ĐẾN VỚI**

**DỰ ÁN MINI-WMS**

*FreshLink Produce — Hệ thống quản lý kho nông sản*

# **1\. Vì sao dự án này tồn tại**

Đây là một dự án demo nội bộ — mô phỏng gần sát nhất có thể với một dự án WMS (Warehouse Management System) thật, cho một khách hàng giả định tên là “FreshLink Produce”, chuyên phân phối nông sản.

Có 3 lý do dự án này tồn tại:

* **Để bạn học nghiệp vụ kho thật:** tồn kho không đơn giản như một con số. Có những quy tắc mà nếu làm sai, doanh nghiệp thật sẽ mất tiền thật.
* **Để bạn có một sản phẩm thật trong tay:** một repo chạy được, có test, có CI — thứ bạn có thể đưa vào CV để phỏng vấn sau này.
* **Để leader và mentor hiểu bạn:** đây là cơ sở thật để đánh giá ai hợp BE, FE, BA hay QA — trước khi xếp vào một dự án khách hàng thật.

# **2\. Bạn sẽ xây gì?**

Một hệ thống quản lý kho thu nhỏ (Mini-WMS), theo đúng luồng vận hành của một kho nông sản thật:

| Luồng nghiệp vụ end-to-end NHẬN HÀNG  →  CẤT HÀNG  →  PHÂN BỔ TỒN  →  SOẠN HÀNG  →  ĐÓNG GÓI  →  GIAO HÀNG  →  (TRẢ HÀNG nếu có) |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------- |

&nbsp;

Công nghệ sử dụng (đã chốt, không đổi):

* **Backend:** NestJS (TypeScript)
* **Database:** PostgreSQL 16 \+ Prisma ORM
* **Frontend:** React \+ TypeScript trên Next.js, ưu tiên giao diện mobile-first cho màn hình vận hành
* **Hạ tầng:** Docker Compose \+ GitHub Actions CI

Nếu bạn chưa từng dùng NestJS hay Prisma — không sao. Tuần 1 là để làm quen, không ai bắt bạn biết sẵn.

# **3\. 8 “bí kíp” nghiệp vụ kho bạn sẽ học được**

Đây là phần giá trị nhất của cả chương trình — quan trọng hơn cả code. Rất nhiều lập trình viên biết code giỏi nhưng KHÔNG biết những điều dưới đây, và đó là lý do phần mềm quản lý kho của họ sai trong thực tế.

**1\. Tồn khả dụng ≠ Tồn vật lý**

*Kho có 100kg cà chua, nhưng 80kg đã bị đơn khác “giữ chỗ” rồi. Đơn mới chỉ được đặt tối đa 20kg — không phải 100kg.*

**2\. Đơn vị tính phải quy đổi đúng**

*Khách đặt theo thùng, kho đếm theo kg. Đặt 5 thùng (1 thùng \= 12kg) mà bạn ghi thẳng số “5” vào kho là ghi sai — phải ghi 60kg.*

**3\. FEFO, không phải FIFO**

*Hàng tươi phải xuất lô nào hết hạn TRƯỚC, không phải lô nào nhập TRƯỚC. Hai thứ này nghe giống nhưng hoàn toàn khác nhau.*

**4\. Catch weight (cân thực tế)**

*Đặt 10kg thịt, cân thực tế chỉ 9,7kg. Phải trừ kho và tính tiền theo số cân THẬT, không theo số đặt.*

**5\. Thiếu hàng có 3 cách xử lý**

*Không chỉ là báo lỗi. Có thể: giao thiếu, đổi hàng thay thế, hoặc hẹn giao bù sau — mỗi cách ảnh hưởng tồn kho khác nhau.*

**6\. Sửa tồn kho phải có người duyệt**

*Nhân viên kho phát hiện thiếu hàng KHÔNG được tự sửa số cho khớp — phải có người khác duyệt. Đây là nguyên tắc chống gian lận.*

**7\. Tồn đầu kỳ phải chống chạy trùng**

*Khi hệ thống mới go-live, import tồn có sẵn 2 lần do vô tình bấm nhầm sẽ làm tồn kho nhân đôi vĩnh viễn nếu không có cơ chế chặn.*

**8\. Đồng thời (concurrency)**

*Hai nhân viên cùng lấy hàng ở một ô kho trong cùng một giây. Code chạy đúng trên máy cá nhân vẫn có thể ra tồn kho âm trên hệ thống thật.*

Bạn không cần hiểu hết ngay bây giờ. Mỗi tuần sẽ có một buổi “business clinic” 45 phút để một bạn trong nhóm trình bày lại một quy tắc — bạn sẽ hiểu sâu dần qua từng tuần, kể cả khi lúc đầu code sai.

# **4\. Đội của bạn sẽ làm việc thế nào**

Đây là điểm khác biệt lớn nhất so với một chương trình intern thông thường: Team 5 người. Team dựng lại REPO được cung cấp sẵn và tự làm TOÀN BỘ tính năng của Mini-WMS.

Team 5 người, vai trò gợi ý là 2 Backend \+ 2 Frontend \+ 1 bạn kiêm BA/QA. Vì chỉ có 2 Backend phải phủ toàn bộ nghiệp vụ (sổ cái, nhập kho, điều chỉnh, phân bổ, soạn/đóng, giao, trả...), cách chia nội bộ hợp lý là: 1 bạn lo trục NHẬP (sổ cái tồn kho, master data, nhập kho, điều chỉnh), 1 bạn lo XUẤT (phân bổ, thiếu hàng, soạn/đóng, giao, trả). Team sẽ tự phân chia công việc cho nhau sao cho phù hợp.

Một vài nguyên tắc làm việc chung, áp dụng như nhau cho 2 team:

* 2 team KHÔNG dùng chung repo, KHÔNG xem code hay copy giải pháp của nhau trong lúc làm — vì đây là bài so sánh năng lực, không phải làm chung một sản phẩm.
* Trong mỗi team, mọi Pull Request cần ít nhất 1 bạn CÙNG team review — không thể review chéo giữa 2 team vì đó là 2 dự án riêng.
* Mỗi team có một bạn giữ vai trò “Trưởng nhóm” module lõi tồn kho (InventoryLedgerService) của team mình xuyên suốt 5 tuần — mọi thay đổi đụng đến module này phải qua bạn đó duyệt trước.
* Mentor và PO/BA dùng CHUNG cho cả 2 team, chia đều thời gian, không thiên vị. Mentor KHÔNG đưa lời giải trước cho bất kỳ team nào — để bạn tự thử, tự sai, gặp bug thật, rồi mới được chỉ nguyên nhân gốc.
* Nhịp làm việc: mỗi team tự standup 15 phút mỗi ngày (riêng) · tech review \+ business clinic thứ Tư (chung cho cả 2 team) · demo \+ retro cuối mỗi tuần xây dựng (mỗi team demo phần của mình).

&nbsp;

*Một điều quan trọng: mục tiêu của việc so sánh 2 team là để ĐÁNH GIÁ NĂNG LỰC CÁ NHÂN nhằm xếp bạn vào đúng vị trí sau này — không phải để phân định “thắng – thua”. Tinh thần thi đua nên là động lực để cả 2 team làm tốt hơn, không phải áp lực tiêu cực.*

# **5\. Hành trình 5 tuần**

&nbsp;

| Tuần             | Trọng tâm                                                                                                                                                       | Cuối tuần bạn sẽ thấy được                                                                                                              |
| :---------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Tuần 1** | Học nghiệp vụ kho\+ dựng nền tảng kỹ thuật RIÊNG cho team bạn (repo, Docker, CI). Chưa code tính năng.                                               | Bạn thuyết trình lại được luồng kho cho mentor nghe — đây là cổng chặn CHUNG cho cả 2 team, không qua thì chưa sang tuần 2\. |
| **Tuần 2** | Đăng nhập/phân quyền, danh mục kho/hàng, xây “sổ cái tồn kho” — trái tim của cả hệ thống, phải xong trước mới làm được các phần sau. | Team bạn đăng nhập được, tạo được kho/SKU, và có một service duy nhất ghi mọi thay đổi tồn kho.                              |
| **Tuần 3** | Team bạn tự chọn thứ tự: nhập hàng, cất hàng, điều chỉnh tồn có phê duyệt, kiểm kê, mã QR — không nhất thiết phải làm hết.              | DEMO 1 (mỗi team demo riêng phần mình): nhập một phiếu hàng thật → tồn kho tăng đúng chỗ → xem lại được lịch sử.          |
| **Tuần 4** | Tuần nặng nhất: phân bổ hàng theo hạn dùng (FEFO), xử lý thiếu hàng, soạn & đóng gói — đòi hỏi nhiều người nhất trong team.               | DEMO 2 (mỗi team demo riêng): một đơn hàng 5 dòng, thiếu 1 dòng → xử lý thiếu hàng → đóng gói → cân thực tế.              |
| **Tuần 5** | Giao hàng, trả hàng, hoàn thiện phần đã làm, sửa bug, viết tài liệu — ưu tiên làm CHẮC hơn là ôm thêm tính năng mới.                     | DEMO DAY: CẢ 2 TEAM trình bày trước đội dự án thật, so sánh trực tiếp\+ nhận đánh giá cuối kỳ.                               |

&nbsp;

# **6\. Vài quy tắc “sống còn” cần nhớ từ ngày đầu**

* **Một cửa duy nhất:** Mọi thay đổi tồn kho chỉ được đi qua một service duy nhất (InventoryLedgerService). Không bao giờ tự ý UPDATE thẳng vào bảng tồn kho ở chỗ khác.
* **Sổ cái không được sửa:** Bảng ghi lịch sử tồn kho (stock\_ledger) chỉ được thêm mới, không bao giờ sửa hay xoá. Ghi sai thì ghi thêm một bút toán đảo để sửa lại — giống hệt kế toán thật.
* **Không dùng dữ liệu khách thật:** Toàn bộ dự án dùng tên khách hàng giả định “FreshLink Produce”. Không đưa tên khách hàng, đối tác, số tiền hay timeline thật của công ty vào repo, Notion hay slide.
* **Đây là sandbox học tập:** Code trong dự án này KHÔNG được mang thẳng vào dự án khách hàng thật — nó dùng để học và đánh giá năng lực.

# **7\. Bạn sẽ được đánh giá thế nào**

Bạn được chấm điểm vào cuối tuần 2, tuần 4 và tuần 5 — không đợi đến cuối chương trình mới biết mình đang ở đâu. Điểm tổng kết dựa trên 8 tiêu chí, không chỉ code:

* Chất lượng code & test
* Khả năng debug độc lập
* Chất lượng khi review PR của người khác
* Hiểu quy tắc nghiệp vụ kho (mục 3 ở trên\!)
* Dám đặt câu hỏi khi yêu cầu chưa rõ ràng
* Ước lượng thời gian làm việc sát thực tế
* Chủ động báo sớm khi bị chặn/tắc, không im lặng ngồi chờ
* Giao tiếp tốt trong standup và các buổi demo

Kết quả ảnh hưởng trực tiếp đến việc bạn có được đề xuất offer full-time hoặc tham gia dự án khách hàng thật sau chương trình hay không — vì vậy đừng ngại hỏi, đó cũng là một tiêu chí được chấm điểm.

*Ngoài điểm cá nhân, leader cũng sẽ tổng hợp một bức tranh so sánh giữa 2 team (số tính năng hoàn thành, kết quả UAT, điểm trung bình team). Đây là dữ liệu để leader hiểu rõ hơn cách mỗi team vận hành — không phải để xếp hạng “ai giỏi hơn ai” một cách đơn giản.*

# **8\. Trước buổi kickoff, bạn nên chuẩn bị**

* Cài sẵn Docker Desktop, Node.js, và một trình soạn code (VS Code khuyến nghị).
* Đọc lại kiến thức SQL cơ bản: SELECT, JOIN, khoá ngoại — vì cả nhóm sẽ làm việc rất nhiều với PostgreSQL.
* Đọc lại mục 3 (8 quy tắc nghiệp vụ) một lần nữa — càng hiểu trước, tuần 1 càng nhẹ nhàng.
* Chuẩn bị sẵn câu hỏi cho buổi kickoff — không có câu hỏi nào là ngớ ngẩn cả.

&nbsp;

| Hẹn gặp bạn ở buổi kickoff\! Không cần hiểu hết tài liệu này ngay. Chỉ cần nắm được bức tranh lớn: chúng ta đang xây gì, vì sao nó khó, và 5 tuần tới sẽ trông như thế nào. Phần còn lại, leader và mentor sẽ đồng hành cùng bạn. |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

&nbsp;
