+++
title = "Ngày 02 - 22/09/2026 (Remote)"
weight = 2
+++

# Báo cáo ngày 02

## 1. Mục tiêu học tập hôm nay

Hôm nay em tập trung tìm hiểu các yêu cầu công nghệ và yêu cầu nghiệp vụ của dự án Mini-WMS. Mục tiêu của em là chuyển mô tả dự án thành một thiết kế kỹ thuật hợp lý, đồng thời xác định các actor chính, luồng người dùng và các ràng buộc hệ thống trước khi bắt đầu triển khai tính năng.

## 2. Những gì em đã làm

- Đọc lại mô tả dự án FreshLink Produce và làm rõ mục tiêu sản phẩm.
- Tìm hiểu stack công nghệ bắt buộc: NestJS, PostgreSQL 16, Prisma, React + TypeScript + Next.js, Docker Compose và GitHub Actions.
- Xác định luồng nghiệp vụ chính của kho: nhận hàng → cất hàng → phân bổ → soạn hàng → đóng gói → giao hàng → trả hàng.
- Phân tích các yêu cầu chức năng chính liên quan đến vận hành kho và quản lý tồn kho.
- Xác định các actor chính trong hệ thống và trách nhiệm của từng actor.
- Tóm tắt các yêu cầu phi chức năng quan trọng về độ tin cậy, truy nguyên và tính toàn vẹn dữ liệu.
- Kết nối các quy tắc nghiệp vụ trong đề cương dự án với các yêu cầu kỹ thuật như sổ cái tồn kho, kiểm soát đồng thời và lịch sử thay đổi.

## 3. Kiến thức đã học

### 3.1 Yêu cầu công nghệ của dự án

Dựa trên tài liệu dự án, hệ thống cần được xây dựng như một giải pháp quản lý kho thực tế cho nhà phân phối hàng tươi. Stack công nghệ được chọn không chỉ để làm demo CRUD, mà để hỗ trợ các hoạt động nghiệp vụ phức tạp.

Stack yêu cầu gồm:

- Backend: NestJS với TypeScript
- Database: PostgreSQL 16
- ORM: Prisma
- Frontend: React + TypeScript trên Next.js
- Hạ tầng: Docker Compose
- CI/CD: GitHub Actions

Những công nghệ này phù hợp vì hệ thống sẽ phải xử lý:

- giao dịch nghiệp vụ,
- logic biến động tồn kho phức tạp,
- lịch sử nhật ký kho và audit trail,
- phân quyền người dùng theo vai trò,
- API backend cho hoạt động kho,
- giao diện cho nhân sự vận hành và quản lý.

### 3.2 Yêu cầu nghiệp vụ và logic kho

Hệ thống được xây dựng quanh luồng vận hành thực tế của kho hàng tươi. Quá trình này không chỉ là lưu trữ hàng hóa, mà là chuỗi hoạt động ảnh hưởng trực tiếp đến độ chính xác tồn kho và chất lượng phục vụ khách hàng.

Luồng nghiệp vụ chính bao gồm:

1. Nhận hàng
2. Cất hàng vào vị trí lưu trữ
3. Phân bổ tồn cho đơn hàng
4. Soạn hàng
5. Đóng gói
6. Giao hàng
7. Xử lý trả hàng khi có

Các quy tắc nghiệp vụ cho thấy dự án tập trung vào độ đúng của hoạt động vận hành hơn là vẻ ngoài giao diện. Hệ thống phải xử lý:

- tồn khả dụng không đồng nghĩa với tồn vật lý,
- quy đổi đơn vị tính đúng cách,
- FEFO thay vì FIFO với hàng tươi,
- catch weight theo số lượng thực tế cân được,
- thiếu hàng có thể xử lý bằng giao thiếu, đổi hàng hoặc hẹn giao sau,
- điều chỉnh tồn kho cần có người duyệt,
- ngăn nhập tồn đầu kỳ trùng lặp,
- kiểm soát đồng thời để tránh tồn kho âm.

Những quy tắc này chuyển thành yêu cầu kỹ thuật về kiểm tra hợp lệ, xử lý ledger, bảo toàn giao dịch và khả năng truy nguyên.

## 4. Các actor chính trong hệ thống Mini-WMS

Dự án có nhiều actor chính, mỗi actor có vai trò khác nhau trong quy trình kho.

### 4.1 Quản trị viên kho / Administrator

Actor này quản lý dữ liệu master và cấu hình hệ thống. Trách nhiệm gồm:

- quản lý cấu hình kho,
- tạo và cập nhật thông tin SKU, sản phẩm,
- định nghĩa vị trí lưu kho hoặc ô hàng,
- quản lý tài khoản người dùng và vai trò,
- kiểm soát quyền truy cập vào các chức năng tồn kho.

### 4.2 Nhân viên kho / Warehouse Operator

Đây là actor chính trong vận hành hàng ngày. Họ thực hiện:

- nhận hàng,
- cất hàng,
- kiểm tra tồn kho,
- soạn và đóng gói đơn hàng,
- xác nhận vận động hàng hóa,
- báo cáo sai lệch cho cấp trên.

### 4.3 Quản lý tồn kho / Approver

Actor này rất quan trọng vì kho không thể cho phép ai cũng tự sửa số lượng tồn luôn. Trách nhiệm gồm:

- phê duyệt điều chỉnh tồn kho,
- kiểm tra thiếu hàng và sai lệch,
- xác nhận các ngoại lệ,
- duyệt quyết định điều chỉnh trước khi lưu.

Vai trò này giúp ngăn gian lận và giữ kiểm soát vận hành.

### 4.4 Nhà cung cấp / Supplier

Nhà cung cấp là bên đưa hàng vào kho. Trong hệ thống, họ được biểu diễn qua:

- thông tin đơn nhập hàng,
- số lượng hàng hóa được giao,
- dữ liệu nhập kho và đối chiếu giao nhận.

### 4.5 Khách hàng / Order Holder

Khách hàng tạo nhu cầu hàng và tạo ra các đơn cần giao. Họ tác động đến:

- đặt hàng,
- phân bổ tồn,
- soạn hàng,
- giao hàng và xử lý các trường hợp phát sinh.

### 4.6 Đối tác vận chuyển / Delivery Partner

Actor này chịu trách nhiệm vận chuyển hàng ra khỏi kho. Vai trò của họ liên quan đến:

- xác nhận giao hàng,
- trạng thái vận chuyển,
- nhận hàng trả lại khi cần thiết.

### 4.7 Hệ thống / Inventory Ledger Service

Dù không phải người dùng trực tiếp, đây là actor kỹ thuật quan trọng nhất của dự án. Service này đóng vai trò “một đầu vào duy nhất” cho mọi thay đổi tồn kho. Nó:

- ghi lại mọi biến động tồn kho,
- kiểm tra tính hợp lệ của cập nhật,
- ngăn sửa trực tiếp vào bảng tồn kho,
- đảm bảo truy nguyên và lịch sử audit.

Đây là actor cốt lõi của hệ thống.

## 5. Yêu cầu chức năng rút ra từ dự án

Dựa trên tài liệu đề cương, hệ thống phải thỏa mãn các yêu cầu chức năng sau.

### 5.1 Quản lý dữ liệu master và kho

- Hệ thống phải quản lý kho, vị trí lưu trữ, SKU và thông tin sản phẩm.
- Số lượng hàng hóa phải có quy đổi đơn vị đúng.
- Dữ liệu master phải chính xác và dễ truy nguyên.

### 5.2 Hoạt động nhập hàng

- Hệ thống phải hỗ trợ nhận hàng từ nhà cung cấp hoặc đơn hàng nhập.
- Mỗi phiếu nhập cần ghi đúng số lượng và thông tin lô/ hạn sử dụng khi cần thiết.
- Tồn kho phải tăng qua service sổ cái đúng chuẩn.

### 5.3 Cất hàng và lưu trữ

- Hàng nhận về phải được gán vào vị trí lưu trữ phù hợp.
- Hệ thống cần hỗ trợ truy vết hàng theo vị trí và lô hàng.
- Hoạt động cất hàng phải được ghi lại trong nhật ký biến động tồn kho.

### 5.4 Phân bổ và giữ chỗ hàng

- Tồn kho phải được phân bổ theo số lượng khả dụng, không chỉ theo tổng tồn.
- Hệ thống phải xét FEFO và số lượng thực tế có thể dùng cho hàng tươi.
- Hàng đã phân bổ không được xem là tồn kho tự do cho đơn khác.

### 5.5 Soạn hàng và đóng gói

- Hệ thống phải hỗ trợ soạn hàng theo đơn đặt.
- Hoạt động soạn hàng phải phản ánh đúng lượng thực tế và tránh tồn kho âm.
- Đóng gói phải đi kèm với trạng thái giao hàng cuối cùng của đơn.

### 5.6 Giao hàng và trả hàng

- Đơn hàng cần có luồng trạng thái rõ ràng từ soạn hàng đến giao nhận.
- Hệ thống phải xử lý thiếu hàng và hoàn hàng một cách hợp lý.
- Khi giao hoặc trả hàng, số lượng tồn phải cập nhật đồng bộ qua sổ cái.

### 5.7 Điều chỉnh và phê duyệt

- Mọi điều chỉnh tồn kho phải có quy trình phê duyệt.
- Sự phê duyệt phải được lưu lại để kiểm toán.
- Hệ thống phải ngăn sửa trái phép trên bảng tồn kho trực tiếp.

## 6. Yêu cầu phi chức năng

Dự án cũng có nhiều yêu cầu phi chức năng quan trọng.

### 6.1 Tính toàn vẹn dữ liệu

Hệ thống phải đảm bảo số lượng tồn kho được ghi đúng và có thể truy nguyên. Không được phép cập nhật trực tiếp vì sẽ làm mất tính nhất quán dữ liệu kho.

### 6.2 Bảo đảm giao dịch

Mọi thao tác liên quan đến biến động tồn kho cần thực hiện như một giao dịch nguyên tử. Nếu có lỗi, dữ liệu phải không để lại trạng thái nửa chừng.

### 6.3 Khả năng kiểm toán

Mọi thay đổi tồn kho đều phải có nhật ký. Điều này cần cho việc đối chiếu, giải quyết tranh chấp và kiểm kiểm soát vận hành.

### 6.4 Kiểm soát đồng thời

Vì nhiều người có thể cùng thao tác trên một vị trí kho trong cùng thời điểm, hệ thống phải dùng cơ chế concurrency đúng để tránh tồn kho âm hay dữ liệu sai lệch.

### 6.5 Bảo mật và phân quyền

Các actor cần có quyền khác nhau. Ví dụ, nhân viên kho không được quyền tự duyệt điều chỉnh tồn kho nếu không có vai trò phù hợp.

### 6.6 Khả năng bảo trì

Hệ thống phải được tổ chức rõ ràng để hỗ trợ làm việc nhóm 5 người và review logic nghiệp vụ hiệu quả.

## 7. Kết nối giữa yêu cầu và thiết kế kỹ thuật

Dự án này cho thấy các yêu cầu không chỉ là các màn hình và tính năng; đó là các quy tắc nghiệp vụ được mã hóa vào thiết kế hệ thống.

Ví dụ:

- sổ cái tồn kho là phản ứng kỹ thuật cho nguyên tắc mọi thay đổi tồn kho phải đi qua một điểm kiểm soát duy nhất,
- điều chỉnh tồn kho cần phê duyệt là cách đáp ứng nhu cầu trách nhiệm và chống gian lận,
- FEFO là quy tắc nghiệp vụ biến thành logic phân bổ và soạn hàng,
- kiểm soát đồng thời là yêu cầu bắt buộc trong môi trường kho có nhiều người thao tác đồng thời.

Điều này cho thấy vì sao dự án là một ví dụ tốt về cách triển khai phần mềm nên dựa trên nghiệp vụ thật chứ không chỉ làm UI đẹp.

## 8. Những thách thức và lưu ý

- Hệ thống có nhiều quy tắc đơn giản về mặt mô tả nhưng khó thực hiện chính xác.
- Một số yêu cầu cần mô hình dữ liệu và logic rất cẩn thận, đặc biệt là biến động tồn kho và lịch sử sổ cái.
- Có nguy cơ chỉ tập trung vào code mà quên hiểu quy trình kho thực tế.
- Nhóm cần phân rõ vai trò, đặc biệt là module InventoryLedgerService và quy trình phê duyệt.

## 9. Kết luận

Ngày 02 là ngày quan trọng vì em đã rời xa phần thiết lập ban đầu và bắt đầu hiểu rõ hơn yêu cầu kỹ thuật và nghiệp vụ thật của dự án Mini-WMS. Em nhận ra đây không phải là hệ thống CRUD đơn thuần, mà là hệ thống kho có nhiều quy tắc vận hành, yêu cầu truy nguyên mạnh và kiểm soát chặt chẽ quanh biến động tồn kho.

Điều quan trọng nhất là hệ thống phải chạy theo nghiệp vụ thực tế. Kiến trúc cần hỗ trợ hoạt động kho thật, còn các actor phải được định nghĩa rõ để trách nhiệm, phân quyền và quy trình làm việc nhất quán với nhau.

Hiểu rõ điều này sẽ là nền tảng quan trọng cho các bước triển khai tiếp theo, vì mọi tính năng ta viết đều phải phù hợp với yêu cầu nghiệp vụ và mô hình hệ thống của dự án.

## 10. Phản ánh cá nhân

Em nên tiếp tục nghiên cứu sâu hơn các yêu cầu của dự án, đặc biệt là 8 quy tắc nghiệp vụ kho và vai trò của InventoryLedgerService. Càng hiểu rõ nghiệp vụ, em càng dễ thiết kế giải pháp kỹ thuật đúng và giảm sai sót trong quá trình triển khai.
