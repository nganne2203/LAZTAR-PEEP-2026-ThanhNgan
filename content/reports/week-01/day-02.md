+++
title = "Day 02 - React and Next.js"
weight = 2
+++

# Daily Report - Day 02

## Learning objective

Study React and Next.js fundamentals in preparation for the Week 2 personal-page exercise: component-based UI, routing, rendering choices, and web presentation.

## 1. React fundamentals

### What is React?

React is a JavaScript library for building user interfaces from reusable components. It focuses on the UI layer; routing, server APIs, and build tooling are normally added through other libraries or frameworks.

### Components and JSX

A component is an independent UI unit that receives data and returns UI. Function components are the modern, common approach; class components are an older but still supported approach. JSX is a JavaScript syntax extension for HTML-like UI markup, with JavaScript expressions inside `{}`.

### Props and state

Props are inputs passed from a parent to a child component and must not be mutated by the child. State is data owned by a component; updating it through a setter asks React to render the UI again. Props are owned by the parent, while state is owned by the component or state store that manages it.

### Virtual DOM

The Virtual DOM is a JavaScript representation of the UI. When props or state change, React compares the new UI tree with the previous tree and applies the needed changes to the real DOM. This supports declarative UI code and reduces direct DOM manipulation.

### Hooks, `useState`, and `useEffect`

Hooks let function components use React features. Common Hooks include `useState`, `useEffect`, `useContext`, `useReducer`, `useRef`, `useMemo`, and `useCallback`.

- `useState` creates local state and its setter, for example `const [count, setCount] = useState(0)`.
- `useEffect` synchronizes a component with an external system, such as an event listener, timer, WebSocket, or client-side API call. An effect can return a cleanup function.

Hooks must be called at the top level of a component or custom Hook, never inside a condition or loop.

### Component lifecycle

The lifecycle can be described as **mount** (the component appears), **update** (props or state change), and **unmount** (the component is removed). In function components, `useEffect` runs after UI is committed, and its cleanup runs before the next effect or on unmount.

### CSR, React Router, Context API, and SPA

**Client-Side Rendering (CSR)** loads JavaScript in the browser, which then renders or updates the UI. **React Router** is a popular library that maps URLs to components and provides client-side navigation. React core does not include a router, SSR/SEO framework, or API server; applications can combine it with React Router, a separate backend, or Next.js.

The **Context API** shares data across a component tree without prop drilling; it is suitable for a theme, locale, or current-user information. Avoid placing all frequently changing state in one large context because it can trigger unnecessary renders.

An **SPA** loads an application shell once and changes screens mainly with client-side navigation. It does not necessarily mean CSR-only: the initial load can still use SSR or SSG.

## 2. React compared with Next.js

| Topic | React | Next.js |
| --- | --- | --- |
| Nature | UI library | Framework built on React |
| Routing | Chosen separately, often React Router | Built-in file-based routing |
| Rendering | Commonly CSR with Vite; SSR needs setup/framework | Static, server rendering, streaming, and client rendering |
| SEO | Depends on rendering and metadata setup | Built-in pre-rendering and Metadata API |
| Structure | No required structure | Conventions such as `app/`, `pages/`, `page.tsx`, `layout.tsx` |
| Server API | Separate backend needed | Route Handlers/API Routes available |

Next.js does not replace React: it uses React for UI and adds full-stack conventions and features. It is often a good fit for multi-page websites, SEO, metadata, server/static rendering, or image optimization. Plain React fits client applications, embedded UI, or projects that already have routing and backend architecture.

For first load, a CSR-only React application commonly needs to load and run JavaScript before the full UI is available. Next.js can send rendered HTML, stream content, and load client JavaScript only for interactive areas; actual performance still depends on bundle size, data fetching, and caching.

## 3. Next.js

### App Router and Pages Router

The **App Router** uses `app/`, Server Components, layouts, and modern conventions, and is suited to new features. The **Pages Router** uses `pages/` and includes APIs such as `getStaticProps` and `getServerSideProps`, which are common in existing projects.

### Server Components and Client Components

In the App Router, pages and layouts are Server Components by default: they can fetch server-side data, use secrets, and do not add their component JavaScript to the client bundle. A Client Component starts with `'use client'` and is used for state, event handlers, effects, or browser APIs. Props that cross the server-client boundary must be serializable.

### SSR, SSG, and ISR

| Strategy | How it works | Suitable use |
| --- | --- | --- |
| SSR | Renders HTML on the server for every request | Fresh request data, personalization, cookies/headers |
| SSG | Creates HTML at build time and serves it from cache/CDN | Documentation, blogs, and stable landing pages |
| ISR | Refreshes a static page on a revalidation interval | Periodically updated content without a full rebuild |

### Routing, dynamic routes, and layouts

Next.js creates URLs from folders and files. For example, `app/about/page.tsx` creates `/about`. A dynamic route uses brackets, such as `app/products/[id]/page.tsx` for `/products/123`; `[...slug]` is a catch-all route. `layout.tsx` defines shared UI, such as a header, navigation, or provider, for a route segment and its child routes.

### Route Handlers and data fetching

In the App Router, a Route Handler is a `route.ts` file inside `app/` that exports HTTP functions such as `GET`, `POST`, `PUT`, `PATCH`, and `DELETE`. Do not place `route.ts` and `page.tsx` in the same route segment. Pages Router API Routes are placed in `pages/api`.

`getStaticProps` and `getServerSideProps` belong only to the Pages Router: the first gets build-time props for static pages, while the second runs on every request for dynamic data. In the App Router, data is fetched in Server Components with cache and revalidation configuration.

### Images, navigation, and Middleware

`next/image` extends `<img>` with image optimization, appropriate sizing, and lazy loading. Provide `width`/`height` or `fill`, and configure valid remote image sources to avoid rendering errors and layout shift.

Use `<Link href="/about">` for internal links to benefit from prefetching and client-side transitions. For programmatic navigation in an App Router Client Component, use `useRouter` from `next/navigation`.

Middleware runs before a request completes. It can redirect, rewrite, modify headers, or return a response. It is suitable for lightweight authentication checks, locale handling, and redirects, not heavy database queries.

### Metadata, TypeScript, and deployment

In the App Router, export `metadata` for static metadata or `generateMetadata` for dynamic metadata from `layout.tsx` or `page.tsx`. Next.js generates the related `<head>` tags and supports file conventions for favicons, Open Graph images, `robots.txt`, and sitemaps. SEO also requires useful content, accurate metadata, and appropriate canonical URLs.

Next.js has built-in TypeScript support for `.ts` and `.tsx` files. It can be deployed to Vercel, a Node.js server, Docker/containers, or a Node.js-compatible cloud provider. A static host is suitable only for static export; SSR, Route Handlers, and Middleware need a compatible runtime.

## Conclusion

React provides the component-based UI foundation, while Next.js extends React with routing, rendering, and production web tooling. These concepts provide the basis for selecting technology and implementing the Week 2 landing page or personal website.
