+++
title = "Ngày 02 - React và Next.js"
weight = 2
+++

# Báo cáo ngày 02

## Mục tiêu học tập

Tìm hiểu kiến thức nền tảng về React và Next.js để chuẩn bị xây dựng trang cá nhân theo hướng dẫn Tuần 2: component hóa giao diện, tổ chức route, chọn chiến lược rendering và tối ưu khả năng hiển thị trên web.

## 1. React cơ bản

### React là gì?

React là thư viện JavaScript để xây dựng giao diện người dùng bằng các component tái sử dụng. React tập trung vào lớp UI; routing, server API hoặc công cụ build thường được bổ sung bằng thư viện hay framework khác.

### Component và JSX

Component là một đơn vị giao diện độc lập, nhận dữ liệu và trả về UI. Hiện nay function component là cách dùng phổ biến; class component là cách cũ vẫn được hỗ trợ. JSX là cú pháp mở rộng của JavaScript, cho phép viết UI gần với HTML; biểu thức JavaScript được đặt trong dấu `{}`.

### Props và State

Props là dữ liệu component cha truyền cho component con và không được component con sửa trực tiếp. State là dữ liệu nội bộ do component quản lý; khi cập nhật state bằng setter, React sẽ render lại UI. Vì vậy, props thuộc về cha còn state thuộc về component hoặc state store đang quản lý nó.

### Virtual DOM

Virtual DOM là biểu diễn UI bằng JavaScript. Khi props hoặc state đổi, React so sánh cây UI mới với cây trước đó rồi cập nhật những phần cần thiết trên DOM thật. Cách làm này giúp code UI theo hướng khai báo, hạn chế thao tác DOM trực tiếp.

### Hooks, `useState` và `useEffect`

Hooks cho phép function component dùng các khả năng của React. Một số Hook phổ biến là `useState`, `useEffect`, `useContext`, `useReducer`, `useRef`, `useMemo` và `useCallback`.

- `useState` tạo state cục bộ và hàm cập nhật, ví dụ: `const [count, setCount] = useState(0)`.
- `useEffect` dùng để đồng bộ component với hệ thống bên ngoài, như event listener, timer, WebSocket hoặc gọi API ở client. Effect có thể trả về hàm cleanup.

Hook chỉ được gọi ở cấp cao nhất của component hoặc custom Hook; không gọi trong điều kiện hay vòng lặp.

### Lifecycle của component

Vòng đời có thể hiểu gồm ba giai đoạn: **mount** khi component xuất hiện, **update** khi props/state đổi, và **unmount** khi component bị gỡ. Với function component, `useEffect` chạy sau khi UI được commit; cleanup chạy trước effect tiếp theo hoặc khi unmount.

### CSR, React Router, Context API và SPA

**Client-Side Rendering (CSR)** là việc trình duyệt tải JavaScript rồi JavaScript render/cập nhật UI. **React Router** là thư viện phổ biến để ánh xạ URL đến component và điều hướng phía client. React core không có sẵn router, SSR/SEO framework hoặc API server; ứng dụng có thể ghép React với React Router, backend riêng, hoặc Next.js.

**Context API** giúp chia sẻ dữ liệu giữa nhiều component mà không cần truyền props qua từng tầng; phù hợp cho theme, locale hoặc thông tin người dùng. Không nên đặt mọi state thay đổi thường xuyên vào một context lớn vì có thể gây render lại không cần thiết.

**SPA** tải application shell một lần và chuyển màn hình chủ yếu bằng client-side navigation. SPA không nhất thiết chỉ dùng CSR; lần tải đầu vẫn có thể dùng SSR hoặc SSG.

## 2. So sánh React và Next.js

| Tiêu chí | React | Next.js |
| --- | --- | --- |
| Bản chất | Thư viện xây UI | Framework xây trên React |
| Routing | Cần tự chọn, thường dùng React Router | File-based routing có sẵn |
| Rendering | Thường CSR khi dùng Vite; SSR cần tự thiết lập/framework | Hỗ trợ static, server rendering, streaming và client rendering |
| SEO | Phụ thuộc cách thiết lập render và metadata | Có pre-rendering và Metadata API tích hợp |
| Cấu trúc | Không áp đặt | Có convention như `app/`, `pages/`, `page.tsx`, `layout.tsx` |
| Server API | Cần backend riêng | Có Route Handlers/API Routes |

Next.js không thay thế React: Next.js dùng React để xây UI và bổ sung các quy ước cùng tính năng full-stack. Next.js thường có lợi cho website nhiều trang, cần SEO, metadata, server/static rendering hoặc tối ưu ảnh. React thuần phù hợp với client application, embedded UI hoặc dự án đã có kiến trúc routing/backend riêng.

Về First Load, ứng dụng React chỉ CSR thường cần tải và chạy JavaScript trước khi có UI đầy đủ. Next.js có thể gửi HTML đã render, stream nội dung và chỉ tải JavaScript cho phần cần tương tác; hiệu năng thực tế vẫn phụ thuộc bundle, data fetching và cache.

## 3. Next.js

### App Router và Pages Router

**App Router** dùng thư mục `app/`, Server Components, layouts và các quy ước hiện đại; đây là lựa chọn phù hợp cho tính năng mới. **Pages Router** dùng thư mục `pages/` và hỗ trợ các API như `getStaticProps` và `getServerSideProps`, thường gặp trong dự án cũ.

### Server Component và Client Component

Trong App Router, page và layout mặc định là Server Component: có thể lấy dữ liệu phía server, dùng secret và không đưa JavaScript component vào client bundle. Client Component có dòng `'use client'` ở đầu file, dùng khi cần state, event handler, effect hoặc browser API. Props truyền qua ranh giới server-client phải serializable.

### SSR, SSG và ISR

| Chiến lược | Cách hoạt động | Trường hợp phù hợp |
| --- | --- | --- |
| SSR | Render HTML trên server cho mỗi request | Dữ liệu mới theo request, cá nhân hóa, cookie/header |
| SSG | Tạo HTML khi build và phục vụ từ CDN/cache | Tài liệu, blog, landing page ít thay đổi |
| ISR | Làm mới static page theo chu kỳ revalidation | Nội dung cần cập nhật định kỳ mà không rebuild toàn site |

### Routing, Dynamic Route và Layout

Next.js tạo URL từ thư mục/file. Ví dụ `app/about/page.tsx` tạo route `/about`. Dynamic route dùng ngoặc vuông, như `app/products/[id]/page.tsx` cho URL `/products/123`; `[...slug]` là catch-all route. File `layout.tsx` định nghĩa UI chung, như header, navigation hoặc provider, cho một route segment và các route con.

### Route Handlers và data fetching

Trong App Router, Route Handler là file `route.ts` trong `app/`, export các hàm HTTP như `GET`, `POST`, `PUT`, `PATCH` và `DELETE`. Không đặt `route.ts` và `page.tsx` tại cùng route segment. API Routes của Pages Router nằm trong `pages/api`.

`getStaticProps` và `getServerSideProps` chỉ thuộc Pages Router: hàm đầu lấy props khi build cho trang static, hàm sau chạy mỗi request cho dữ liệu động. Trong App Router, data fetching thực hiện trong Server Component cùng cấu hình cache/revalidation.

### Hình ảnh, điều hướng và Middleware

`next/image` mở rộng thẻ `<img>` bằng tối ưu ảnh, kích thước phù hợp và lazy loading. Cần khai báo `width`/`height` hoặc `fill`, đồng thời cấu hình nguồn ảnh remote hợp lệ để tránh lỗi render và layout shift.

Dùng `<Link href="/about">` cho liên kết nội bộ để tận dụng prefetch và client-side transition. Khi cần điều hướng bằng code trong Client Component, dùng `useRouter` từ `next/navigation`.

Middleware chạy trước khi request được hoàn tất; có thể redirect, rewrite, chỉnh header hoặc trả response. Middleware phù hợp cho kiểm tra xác thực sơ bộ, locale và redirect, không phù hợp cho truy vấn database nặng.

### Metadata, TypeScript và Deploy

Trong App Router, export `metadata` cho metadata tĩnh hoặc `generateMetadata` cho metadata động từ `layout.tsx` hay `page.tsx`. Next.js tạo các thẻ `<head>`; đồng thời hỗ trợ file convention cho favicon, Open Graph image, `robots.txt` và sitemap. SEO còn cần nội dung tốt, metadata chính xác và canonical URL phù hợp.

Next.js hỗ trợ TypeScript sẵn có với các file `.ts` và `.tsx`. Dự án có thể deploy lên Vercel, Node.js server, Docker/container hoặc cloud provider hỗ trợ Node.js. Static host chỉ phù hợp khi dùng static export; SSR, Route Handlers và Middleware cần runtime tương thích.

## Kết luận

React cung cấp nền tảng component hóa giao diện, còn Next.js mở rộng React bằng routing, rendering và các công cụ web production. Các kiến thức này là cơ sở để lựa chọn công nghệ và triển khai landing page/trang cá nhân trong bài thực hành Tuần 2.
