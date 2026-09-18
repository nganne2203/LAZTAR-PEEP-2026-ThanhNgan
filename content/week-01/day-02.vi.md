
+++
title = "Day 02 - 16/09/2026 (On-site)"
weight = 2
+++

# Báo cáo ngày 02

## A. Lý thuyết

## Phần 1. React cơ bản

### 1. React là gì?

React là thư viện JavaScript mã nguồn mở dùng để xây dựng giao diện người dùng từ các component có thể tái sử dụng. React tập trung vào tầng giao diện; routing, API server và cách triển khai thường được bổ sung bằng thư viện hoặc framework khác.

### 2. Component trong React là gì? Có mấy loại component?

Component là một khối giao diện độc lập, nhận dữ liệu đầu vào và trả về JSX. Có hai loại component chính:

- **Function Component:** Là hàm JavaScript trả về JSX. Đây là cách viết phổ biến hiện nay và có thể sử dụng Hooks.
- **Class Component:** Là class kế thừa `React.Component`, có phương thức `render()` và các lifecycle methods. Loại này vẫn được hỗ trợ nhưng chủ yếu gặp trong dự án cũ.

### 3. JSX là gì?

JSX là cú pháp mở rộng của JavaScript, cho phép mô tả giao diện bằng cấu trúc gần giống HTML. JSX được biên dịch thành các lời gọi tạo React element. Biểu thức JavaScript được đặt trong `{}`, và JSX phải trả về một cây phần tử hợp lệ.

### 4. Props là gì?

Props là dữ liệu component cha truyền xuống component con. Props giúp cấu hình và tái sử dụng component với dữ liệu khác nhau. Component nhận props chỉ nên đọc, không sửa trực tiếp giá trị props.

### 5. State là gì? State khác Props như thế nào?

State là dữ liệu nội bộ mà component ghi nhớ giữa các lần render. Khi state thay đổi thông qua setter, React lên lịch render lại component.

- **State:** Do component quản lý, có thể cập nhật bằng setter và thường phản ánh dữ liệu thay đổi theo tương tác.
- **Props:** Do component cha truyền xuống, chỉ đọc tại component con và thay đổi khi cha truyền giá trị mới.

### 6. Virtual DOM là gì? Vì sao React sử dụng Virtual DOM?

Virtual DOM là biểu diễn dạng JavaScript của cây giao diện. Khi props hoặc state thay đổi, React tạo cây mới, so sánh với cây trước đó qua quá trình reconciliation, rồi cập nhật phần cần thiết trên DOM thật. Cách này giúp lập trình giao diện theo hướng khai báo, giảm việc thao tác DOM thủ công và gom các cập nhật UI một cách nhất quán.

### 7. Hooks là gì? Kể tên một số Hook phổ biến trong React.

Hooks là các hàm cho phép Function Component sử dụng state, effect, context, ref và các khả năng khác của React. Một số Hook phổ biến:

- **`useState`:** Lưu và cập nhật state cục bộ.
- **`useEffect`:** Đồng bộ component với hệ thống bên ngoài.
- **`useContext`:** Đọc và theo dõi giá trị từ Context.
- **`useReducer`:** Quản lý state có logic cập nhật phức tạp bằng reducer.
- **`useRef`:** Lưu giá trị không gây render lại hoặc tham chiếu DOM.
- **`useMemo`:** Ghi nhớ kết quả tính toán giữa các lần render.
- **`useCallback`:** Ghi nhớ một function giữa các lần render.

Hooks phải được gọi ở cấp cao nhất của Function Component hoặc custom Hook, không gọi trong vòng lặp hay điều kiện.

### 8. `useState` dùng để làm gì?

`useState` khai báo một biến state và hàm cập nhật nó. Ví dụ `const [count, setCount] = useState(0)`. Khi gọi `setCount`, React lưu giá trị mới và render lại component. Không nên sửa trực tiếp object hoặc array đang nằm trong state; cần tạo giá trị mới.

### 9. `useEffect` dùng để làm gì?

`useEffect` dùng để đồng bộ component với hệ thống bên ngoài, ví dụ:

- Gọi hoặc đồng bộ dữ liệu từ API ở phía client.
- Đăng ký và hủy event listener.
- Tạo và xóa timer.
- Kết nối và ngắt WebSocket hoặc thư viện bên thứ ba.

Effect có thể trả về cleanup function. Dependency array xác định khi effect cần chạy lại. Nếu không tương tác với hệ thống bên ngoài, thường không cần dùng effect.

### 10. Lifecycle của một React Component gồm những giai đoạn nào?

Lifecycle của component gồm ba giai đoạn chính:

- **Mounting:** Component được tạo và thêm vào màn hình.
- **Updating:** Component render lại khi props, state hoặc context thay đổi.
- **Unmounting:** Component bị gỡ khỏi màn hình; đây là lúc dọn event listener, timer hoặc kết nối.

Với Function Component, `useEffect` setup việc đồng bộ và cleanup dừng việc đồng bộ. Với Class Component, các lifecycle method thường gặp là `componentDidMount`, `componentDidUpdate` và `componentWillUnmount`.

### 11. Client-Side Rendering (CSR) là gì?

CSR là cách trình duyệt tải JavaScript rồi render giao diện ở phía client. Sau lần tải đầu, ứng dụng có thể cập nhật UI và chuyển trang nhanh mà không tải lại toàn bộ tài liệu HTML. Nhược điểm là nội dung ban đầu có thể xuất hiện chậm nếu bundle lớn và SEO cần được xử lý thêm.

### 12. React Router là gì?

React Router là thư viện routing cho ứng dụng React. Nó ánh xạ URL đến component và hỗ trợ:

- Điều hướng phía client mà không tải lại toàn trang.
- Nested routes để tổ chức giao diện lồng nhau.
- Dynamic routes để nhận tham số URL.
- Đọc query string và quản lý lịch sử điều hướng.

React Router là thư viện độc lập, không nằm trong React core.

### 13. React thuần có hỗ trợ Routing, SEO và API Server không?

React core không cung cấp sẵn các phần này:

- **Routing:** Cần dùng React Router hoặc giải pháp khác.
- **SEO:** Có thể thiết lập metadata ở client, nhưng muốn HTML được pre-render tốt cho crawler thường cần SSR/SSG hoặc framework.
- **API Server:** Cần backend riêng như Express, NestJS hoặc dùng framework full-stack.

### 14. Context API là gì? Khi nào nên sử dụng?

Context API truyền dữ liệu tới nhiều component trong cùng cây mà không cần chuyển props qua từng tầng. Nên dùng cho dữ liệu dùng chung như theme, ngôn ngữ, thông tin đăng nhập hoặc cấu hình ứng dụng. Không nên đặt mọi state thay đổi thường xuyên vào một context lớn vì nhiều consumer có thể render lại; state phức tạp nên được tách context hoặc quản lý bằng công cụ phù hợp.

### 15. SPA (Single Page Application) là gì?

SPA là ứng dụng web tải một application shell rồi thay đổi nội dung chủ yếu bằng JavaScript và client-side navigation. Mỗi lần chuyển route không cần tải lại toàn bộ trang. SPA mang lại trải nghiệm gần ứng dụng desktop nhưng cần chú ý first load, SEO, accessibility và quản lý history. SPA vẫn có thể dùng SSR hoặc SSG cho lần tải đầu.

## Phần 2. So sánh React và Next.js

### 1. Next.js là gì?

Next.js là framework full-stack xây trên React. Nó cung cấp sẵn file-based routing, rendering trên server và tại build time, tối ưu tài nguyên, metadata, Route Handlers và quy trình build/deploy.

### 2. Điểm khác biệt cốt lõi giữa React và Next.js là gì?

- **React:** Là thư viện tạo giao diện bằng component; không quy định đầy đủ cách routing, render server hay tổ chức backend.
- **Next.js:** Là framework sử dụng React và bổ sung convention cùng công cụ để xây dựng ứng dụng web hoàn chỉnh.

### 3. Routing trong React và Next.js khác nhau như thế nào?

- **React:** Không có router tích hợp. Dự án thường cài React Router và khai báo route trong code.
- **Next.js:** Có file-based routing. Thư mục và file như `app/about/page.tsx` tự tạo route `/about`.

### 4. Rendering trong React và Next.js khác nhau ra sao?

- **React thuần:** Thường dùng CSR khi được tạo với Vite hoặc công cụ tương tự. Muốn SSR/SSG cần tự thiết lập hoặc dùng framework.
- **Next.js:** Hỗ trợ static rendering, dynamic server rendering, streaming và client rendering; có thể kết hợp Server Component với Client Component.

### 5. Vì sao Next.js hỗ trợ SEO tốt hơn React thuần?

Next.js có thể gửi HTML đã render và metadata ngay từ server hoặc build time. Search engine nhận được nội dung, title, description, Open Graph và canonical data sớm hơn. React thuần vẫn có thể SEO tốt, nhưng phải tự bổ sung pre-rendering/SSR và quản lý metadata.

### 6. Hiệu năng tải trang đầu tiên của React và Next.js khác nhau như thế nào?

- **React CSR:** Thường phải tải, phân tích và chạy JavaScript trước khi giao diện đầy đủ xuất hiện.
- **Next.js:** Có thể gửi HTML đã render, stream nội dung, prefetch route và giảm JavaScript client bằng Server Components.

Next.js không tự động luôn nhanh hơn; kết quả còn phụ thuộc bundle, hình ảnh, data fetching, cache và cách triển khai.

### 7. Cấu trúc dự án React và Next.js khác nhau ra sao?

- **React:** Không áp đặt cấu trúc; nhóm phát triển tự tổ chức `components/`, `pages/`, `hooks/`, router và API client.
- **Next.js:** Có các convention như `app/` hoặc `pages/`, `public/`, `page.tsx`, `layout.tsx`, `loading.tsx`, `error.tsx` và `route.ts`.

### 8. Next.js có thay thế React không? Vì sao?

Không. Next.js sử dụng React để xây dựng component và giao diện. React là nền tảng UI, còn Next.js là một framework trong hệ sinh thái React, bổ sung routing, rendering và khả năng server.

### 9. Khi nào nên dùng React thuần và khi nào nên dùng Next.js?

- **Dùng React thuần:** Dashboard nội bộ, SPA phía client, widget nhúng, hoặc dự án đã có backend và kiến trúc routing riêng.
- **Dùng Next.js:** Website cần SEO, landing page, blog, thương mại điện tử, ứng dụng cần SSR/SSG/ISR, hoặc dự án muốn đặt UI và server endpoint trong cùng framework.

## Phần 3. Next.js

### 1. App Router và Pages Router trong Next.js là gì?

- **App Router:** Dùng thư mục `app/`; hỗ trợ Server Components, nested layouts, streaming, Route Handlers và các tính năng React mới. Đây là lựa chọn ưu tiên cho dự án mới.
- **Pages Router:** Dùng thư mục `pages/`; mỗi file tương ứng một route và dùng các API như `getStaticProps`, `getServerSideProps`. Vẫn được hỗ trợ cho dự án hiện có.

### 2. Server Component và Client Component khác nhau như thế nào?

- **Server Component:** Mặc định trong App Router; chạy/render trên server, có thể truy cập dữ liệu và secret phía server, giảm JavaScript gửi về trình duyệt. Không dùng state, event handler hoặc browser API.
- **Client Component:** Khai báo bằng `'use client'`; dùng state, Hooks, event handler và API như `window` hoặc `localStorage`. Props nhận từ Server Component phải serializable.

### 3. SSR (Server-Side Rendering) là gì?

SSR tạo HTML trên server cho mỗi request. Nó phù hợp với dữ liệu phải mới theo từng request, nội dung cá nhân hóa hoặc phụ thuộc cookie/header. Đổi lại, server phải xử lý mỗi request và thời gian phản hồi phụ thuộc việc lấy dữ liệu.

### 4. SSG (Static Site Generation) là gì?

SSG tạo HTML trước tại build time và phục vụ từ cache/CDN. Nó phù hợp với landing page, tài liệu hoặc blog ít thay đổi. Ưu điểm là tải nhanh và giảm tải server; nội dung cần build lại hoặc revalidate để cập nhật.

### 5. ISR (Incremental Static Regeneration) là gì?

ISR cho phép làm mới trang static sau một khoảng thời gian hoặc theo yêu cầu mà không build lại toàn bộ website. Công dụng chính:

- Phục vụ phần lớn request bằng trang static nhanh.
- Cập nhật nội dung định kỳ.
- Giảm thời gian build với website có nhiều trang.
- Giảm tải server so với SSR cho mọi request.

### 6. File-based Routing trong Next.js hoạt động như thế nào?

Trong App Router, mỗi thư mục là một route segment và `page.tsx` làm route có thể truy cập. Ví dụ:

- `app/page.tsx` → `/`
- `app/about/page.tsx` → `/about`
- `app/blog/[slug]/page.tsx` → `/blog/:slug`

Các file đặc biệt như `layout.tsx`, `loading.tsx`, `error.tsx` bổ sung giao diện và hành vi cho segment.

### 7. Dynamic Route trong Next.js là gì?

Dynamic Route dùng tên segment trong ngoặc vuông để nhận tham số URL:

- **`[id]`:** Một segment động, ví dụ `/products/123`.
- **`[...slug]`:** Catch-all, nhận một hoặc nhiều segment.
- **`[[...slug]]`:** Optional catch-all, chấp nhận cả trường hợp không có segment.

### 8. `layout.tsx` trong App Router dùng để làm gì?

`layout.tsx` định nghĩa UI dùng chung cho một route segment và các route con. Nó thường chứa header, navigation, footer hoặc provider. Layout lồng nhau theo cấu trúc thư mục, giữ state và không render lại khi điều hướng giữa các page dùng chung layout đó.

### 9. API Routes (Route Handlers) trong Next.js là gì?

Route Handlers tạo HTTP endpoint bằng file `route.ts` trong `app/`. Các method được hỗ trợ gồm:

- **`GET`:** Đọc dữ liệu.
- **`POST`:** Tạo dữ liệu hoặc xử lý submission.
- **`PUT`/`PATCH`:** Cập nhật dữ liệu.
- **`DELETE`:** Xóa dữ liệu.
- **`HEAD`/`OPTIONS`:** Xử lý metadata response hoặc khả năng giao tiếp HTTP.

Trong Pages Router, API Routes nằm ở `pages/api/`.

### 10. `getStaticProps` và `getServerSideProps` là gì? Chúng dùng trong trường hợp nào?

Đây là API của Pages Router:

- **`getStaticProps`:** Chạy khi build để lấy props và tạo trang static; dùng cho dữ liệu có thể cache hoặc ít thay đổi.
- **`getServerSideProps`:** Chạy trên server cho mỗi request; dùng cho dữ liệu mới theo request hoặc nội dung cá nhân hóa.

Hai hàm này không dùng trong App Router. App Router lấy dữ liệu trực tiếp trong Server Components và cấu hình cache/revalidation.

### 11. `next/image` giúp tối ưu hình ảnh như thế nào?

`next/image` hỗ trợ:

- Tạo kích thước ảnh phù hợp với thiết bị.
- Lazy-load ảnh khi ảnh sắp xuất hiện trong viewport.
- Hạn chế layout shift bằng kích thước hoặc tỷ lệ ảnh đã biết.
- Tối ưu ảnh local và remote qua image optimization pipeline.

Ảnh remote phải được cho phép trong `next.config.*`, và cần khai báo `width`/`height` hoặc dùng `fill`.

### 12. Middleware trong Next.js là gì?

Middleware chạy trước khi request hoàn tất và có thể redirect, rewrite, sửa request/response headers hoặc trả response. Trường hợp dùng phổ biến là kiểm tra truy cập sơ bộ, locale và redirect. Không nên thực hiện xử lý chậm hoặc truy vấn database nặng tại đây. Trong các phiên bản Next.js mới, convention này được đổi tên thành **Proxy**, nhưng mục đích chặn và xử lý request trước route vẫn tương tự.

### 13. Làm thế nào để điều hướng giữa các trang trong Next.js?

- **`<Link href="/about">`:** Điều hướng nội bộ theo kiểu khai báo, hỗ trợ prefetch và client-side transition.
- **`useRouter().push()` hoặc `replace()`:** Điều hướng bằng code trong Client Component, ví dụ sau khi submit form.
- **`redirect()`:** Chuyển hướng trong Server Component, Server Action hoặc Route Handler phù hợp.

### 14. Metadata và SEO trong Next.js được xử lý như thế nào?

Trong App Router:

- **`metadata`:** Khai báo metadata tĩnh trong `layout.tsx` hoặc `page.tsx`.
- **`generateMetadata`:** Tạo metadata động từ params hoặc dữ liệu.
- **File conventions:** `favicon.ico`, `opengraph-image`, `twitter-image`, `robots.txt` và `sitemap.xml`.

Next.js tạo các thẻ head tương ứng. SEO vẫn cần nội dung chất lượng, semantic HTML, canonical URL, hiệu năng và accessibility.

### 15. Next.js có hỗ trợ TypeScript không?

Có. `create-next-app` có thể khởi tạo dự án TypeScript, tự cài type cần thiết và tạo cấu hình ban đầu. Next.js hỗ trợ file `.ts`, `.tsx`, type cho page/layout/route và kiểm tra type trong quy trình phát triển hoặc build.

### 16. Có thể deploy dự án Next.js lên những nền tảng nào?

- **Vercel:** Tích hợp trực tiếp với Next.js và Git.
- **Node.js server:** Chạy bằng `next build` và `next start`.
- **Docker/container:** Đóng gói để chạy trên cloud hoặc hạ tầng riêng.
- **Cloud platform có adapter/runtime phù hợp:** Ví dụ AWS, Google Cloud, Azure, Netlify hoặc Cloudflare tùy tính năng và adapter.
- **Static hosting:** Dùng khi dự án có thể static export; không hỗ trợ đầy đủ các tính năng cần server.

Nền tảng triển khai phải hỗ trợ những tính năng dự án sử dụng như SSR, ISR, Route Handlers, image optimization hoặc Proxy/Middleware.

## B. Tổng kết

### Những gì đã học được

- **HTML/CSS:** Dùng HTML có ngữ nghĩa để tổ chức các phần của landing page; dùng Flexbox/Grid, khoảng cách, màu sắc và typography để tạo bố cục nhất quán.
- **React và Next.js:** Chia giao diện thành component tái sử dụng, truyền dữ liệu bằng props và hiểu khi nào cần state. Phân biệt App Router, Server Component và Client Component để chọn cách xây dựng trang phù hợp.
- **Responsive:** Thiết kế bố cục thích ứng bằng CSS media queries; kiểm tra kích thước màn hình trên DevTools và điều chỉnh menu, cột nội dung, chữ và hình ảnh cho thiết bị nhỏ.
- **Tối ưu trang:** Chú ý kích thước ảnh, văn bản thay thế, metadata và các liên kết để trang dễ sử dụng và tải hợp lý.
- **Deploy Vercel:** Hiểu quy trình đưa mã nguồn lên Git, kết nối repository với Vercel, chạy build và kiểm tra trang trên URL đã triển khai.

### Khó khăn gặp phải và cách giải quyết

- **Khó phân biệt React với Next.js và các cách rendering:** Đối chiếu vai trò của thư viện và framework; lập ví dụ riêng cho CSR, SSR, SSG và ISR để chọn cách phù hợp với từng loại nội dung.
- **Bố cục dễ bị tràn hoặc lệch trên màn hình nhỏ:** Kiểm tra từng breakpoint bằng DevTools, cho các cột xếp chồng, điều chỉnh khoảng cách và bảo đảm ảnh không vượt quá chiều rộng vùng chứa.
- **Ảnh hoặc liên kết hoạt động ở local nhưng lỗi sau deploy:** Kiểm tra đường dẫn, cấu hình nguồn ảnh remote khi dùng `next/image`, xem build log trên Vercel và thử lại toàn bộ liên kết trên bản deploy.

## URL PAGE

* Link landing page: [portfolio-nganne2203s-projects.vercel.app](https://portfolio-nganne2203s-projects.vercel.app/)
* Link Repo: [github.com/nganne2203/Portfolio](https://github.com/nganne2203/Portfolio)
