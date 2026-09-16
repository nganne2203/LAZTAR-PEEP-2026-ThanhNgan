+++
title = "Day 02 - React and Next.js"
weight = 2
+++

# Daily Report - Day 02

## A. Theory

## Part 1. React fundamentals

### 1. What is React?

React is an open-source JavaScript library for building user interfaces from reusable components. It focuses on the UI layer; routing, API servers, and deployment are normally provided by other libraries or frameworks.

### 2. What is a React component? How many component types are there?

A component is an independent UI block that receives input and returns JSX. There are two main component types:

- **Function Component:** A JavaScript function that returns JSX. It is the common modern approach and can use Hooks.
- **Class Component:** A class that extends `React.Component`, implements `render()`, and uses lifecycle methods. It remains supported but is mostly found in older projects.

### 3. What is JSX?

JSX is a JavaScript syntax extension that describes UI with HTML-like markup. It is compiled into calls that create React elements. JavaScript expressions are placed inside `{}`, and JSX must return a valid element tree.

### 4. What are props?

Props are values passed from a parent component to a child component. They make components configurable and reusable with different data. A receiving component should read props without mutating them directly.

### 5. What is state? How is state different from props?

State is internal data that a component remembers between renders. Updating state through its setter schedules another render.

- **State:** Managed by the component, updated through a setter, and commonly represents interactive data.
- **Props:** Owned and passed by the parent, read-only in the child, and changed when the parent provides a new value.

### 6. What is the Virtual DOM? Why does React use it?

The Virtual DOM is a JavaScript representation of the UI tree. When props or state change, React creates a new tree, compares it with the previous tree through reconciliation, and updates the necessary parts of the real DOM. This enables declarative UI code, reduces manual DOM manipulation, and coordinates UI updates consistently.

### 7. What are Hooks? Name some common React Hooks.

Hooks are functions that let Function Components use state, effects, context, refs, and other React capabilities. Common Hooks include:

- **`useState`:** Stores and updates local state.
- **`useEffect`:** Synchronizes a component with an external system.
- **`useContext`:** Reads and subscribes to a Context value.
- **`useReducer`:** Manages state with complex update logic in a reducer.
- **`useRef`:** Stores a value without re-rendering or references a DOM node.
- **`useMemo`:** Caches a calculated value between renders.
- **`useCallback`:** Caches a function between renders.

Hooks must be called at the top level of a Function Component or custom Hook, not inside loops or conditions.

### 8. What does `useState` do?

`useState` declares a state variable and its update function. For example, `const [count, setCount] = useState(0)`. Calling `setCount` stores the new value and schedules a render. Objects and arrays in state should be replaced with new values instead of mutated directly.

### 9. What does `useEffect` do?

`useEffect` synchronizes a component with an external system, for example:

- Fetching or synchronizing client-side API data.
- Adding and removing event listeners.
- Starting and clearing timers.
- Connecting to and disconnecting from a WebSocket or third-party library.

An effect can return a cleanup function. Its dependency array determines when synchronization runs again. If no external system is involved, an effect is often unnecessary.

### 10. What stages are in a React component lifecycle?

A component lifecycle has three main stages:

- **Mounting:** The component is created and added to the screen.
- **Updating:** The component renders again when props, state, or context changes.
- **Unmounting:** The component is removed; listeners, timers, and connections should be cleaned up.

In Function Components, `useEffect` sets up synchronization and its cleanup stops it. In Class Components, common methods are `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

### 11. What is Client-Side Rendering (CSR)?

CSR means that the browser loads JavaScript and renders the UI on the client. After the first load, the application can update UI and navigate without downloading a complete new HTML document. Large bundles can delay initial content, and SEO may require additional handling.

### 12. What is React Router?

React Router is a routing library for React applications. It supports:

- Client-side navigation without a full-page reload.
- Nested routes for nested UI.
- Dynamic routes with URL parameters.
- Query-string access and navigation-history management.

React Router is an independent library, not part of React core.

### 13. Does plain React support routing, SEO, and an API server?

React core does not include these features:

- **Routing:** Requires React Router or another solution.
- **SEO:** Client metadata is possible, but crawler-friendly pre-rendered HTML normally requires SSR/SSG or a framework.
- **API server:** Requires a separate backend such as Express or NestJS, or a full-stack framework.

### 14. What is the Context API? When should it be used?

The Context API supplies data to multiple components in a tree without passing props through every level. It suits shared values such as theme, locale, authentication information, or application configuration. Frequently changing state should not all be placed in one large context because many consumers can re-render; complex state can use split contexts or a suitable state-management solution.

### 15. What is an SPA (Single Page Application)?

An SPA loads one application shell and changes content mainly with JavaScript and client-side navigation. Route changes do not require a complete page reload. SPAs provide app-like interaction but must address first load, SEO, accessibility, and browser history. An SPA may still use SSR or SSG for its initial load.

## Part 2. React compared with Next.js

### 1. What is Next.js?

Next.js is a full-stack framework built on React. It provides file-based routing, server and build-time rendering, asset optimization, metadata, Route Handlers, and a build/deployment workflow.

### 2. What is the core difference between React and Next.js?

- **React:** A component-based UI library that does not prescribe complete routing, server rendering, or backend architecture.
- **Next.js:** A framework that uses React and adds conventions and tools for building complete web applications.

### 3. How does routing differ between React and Next.js?

- **React:** Has no built-in router. Projects commonly install React Router and declare routes in code.
- **Next.js:** Has file-based routing. Folders and files such as `app/about/page.tsx` create the `/about` route.

### 4. How does rendering differ between React and Next.js?

- **Plain React:** Commonly uses CSR when created with Vite or a similar tool. SSR/SSG requires additional setup or a framework.
- **Next.js:** Supports static rendering, dynamic server rendering, streaming, and client rendering, and can compose Server Components with Client Components.

### 5. Why does Next.js support SEO better than plain React?

Next.js can send rendered HTML and metadata from the server or build output. Search engines receive content, titles, descriptions, Open Graph data, and canonical information earlier. Plain React can also provide good SEO, but pre-rendering/SSR and metadata management must be added separately.

### 6. How does first-load performance differ between React and Next.js?

- **React CSR:** Commonly loads, parses, and executes JavaScript before the complete UI appears.
- **Next.js:** Can deliver rendered HTML, stream content, prefetch routes, and reduce client JavaScript with Server Components.

Next.js is not automatically faster in every project; bundle size, images, data fetching, caching, and implementation still determine the result.

### 7. How do React and Next.js project structures differ?

- **React:** Imposes no structure; teams organize `components/`, `pages/`, `hooks/`, routing, and API clients themselves.
- **Next.js:** Provides conventions such as `app/` or `pages/`, `public/`, `page.tsx`, `layout.tsx`, `loading.tsx`, `error.tsx`, and `route.ts`.

### 8. Does Next.js replace React? Why?

No. Next.js uses React to build components and UI. React is the UI foundation, while Next.js is a framework in the React ecosystem that adds routing, rendering, and server capabilities.

### 9. When should plain React be used, and when should Next.js be used?

- **Use plain React:** For internal dashboards, client-side SPAs, embedded widgets, or projects that already have separate backend and routing architecture.
- **Use Next.js:** For SEO-sensitive websites, landing pages, blogs, e-commerce, applications requiring SSR/SSG/ISR, or projects that want UI and server endpoints in one framework.

## Part 3. Next.js

### 1. What are the App Router and Pages Router in Next.js?

- **App Router:** Uses `app/`; supports Server Components, nested layouts, streaming, Route Handlers, and modern React features. It is preferred for new projects.
- **Pages Router:** Uses `pages/`; each file maps to a route and can use `getStaticProps` and `getServerSideProps`. It remains supported for existing projects.

### 2. How do Server Components and Client Components differ?

- **Server Component:** The App Router default; renders on the server, can access server data and secrets, and reduces browser JavaScript. It cannot use state, event handlers, or browser APIs.
- **Client Component:** Begins with `'use client'`; can use state, Hooks, event handlers, and APIs such as `window` or `localStorage`. Props received across the server-client boundary must be serializable.

### 3. What is SSR (Server-Side Rendering)?

SSR generates HTML on the server for every request. It suits request-fresh data, personalized content, or values based on cookies and headers. The server must process each request, and response time depends on data retrieval.

### 4. What is SSG (Static Site Generation)?

SSG creates HTML at build time and serves it from a cache or CDN. It suits landing pages, documentation, and stable blogs. It loads quickly and reduces server work, but content requires a rebuild or revalidation to update.

### 5. What is ISR (Incremental Static Regeneration)?

ISR refreshes static pages after a time interval or on demand without rebuilding the entire site. Its purposes are:

- Serving most requests with fast static pages.
- Updating content periodically.
- Reducing build time for sites with many pages.
- Reducing server work compared with SSR on every request.

### 6. How does file-based routing work in Next.js?

In the App Router, every folder is a route segment and `page.tsx` makes the route accessible. Examples:

- `app/page.tsx` → `/`
- `app/about/page.tsx` → `/about`
- `app/blog/[slug]/page.tsx` → `/blog/:slug`

Special files such as `layout.tsx`, `loading.tsx`, and `error.tsx` add UI and behavior to a segment.

### 7. What is a dynamic route in Next.js?

A dynamic route uses a bracketed segment to receive a URL parameter:

- **`[id]`:** One dynamic segment, such as `/products/123`.
- **`[...slug]`:** A catch-all route that receives one or more segments.
- **`[[...slug]]`:** An optional catch-all that also matches no segment.

### 8. What does `layout.tsx` do in the App Router?

`layout.tsx` defines shared UI for a route segment and its children. It commonly contains a header, navigation, footer, or provider. Layouts nest according to the folder tree, preserve state, and do not re-render when navigating between pages that share the layout.

### 9. What are API Routes (Route Handlers) in Next.js?

Route Handlers create HTTP endpoints with a `route.ts` file inside `app/`. Supported methods include:

- **`GET`:** Reads data.
- **`POST`:** Creates data or processes a submission.
- **`PUT`/`PATCH`:** Updates data.
- **`DELETE`:** Deletes data.
- **`HEAD`/`OPTIONS`:** Handles response metadata or HTTP communication capabilities.

In the Pages Router, API Routes live in `pages/api/`.

### 10. What are `getStaticProps` and `getServerSideProps`? When are they used?

These are Pages Router APIs:

- **`getStaticProps`:** Runs at build time to fetch props and generate a static page; use it for cacheable or infrequently changing data.
- **`getServerSideProps`:** Runs on the server for every request; use it for request-fresh or personalized data.

They are not used in the App Router, where Server Components fetch data directly with cache and revalidation configuration.

### 11. How does `next/image` optimize images?

`next/image` supports:

- Delivering an image size appropriate for the device.
- Lazy-loading images as they approach the viewport.
- Preventing layout shift with a known image size or ratio.
- Optimizing local and remote images through the image pipeline.

Remote sources must be allowed in `next.config.*`, and images need `width`/`height` or `fill`.

### 12. What is Middleware in Next.js?

Middleware runs before a request completes and can redirect, rewrite, modify request/response headers, or return a response. Common uses include lightweight access checks, locale handling, and redirects. Slow work or heavy database queries should not run there. In newer Next.js versions, this convention is named **Proxy**, while its role of intercepting requests before routes remains similar.

### 13. How can users navigate between pages in Next.js?

- **`<Link href="/about">`:** Declarative internal navigation with prefetching and client-side transitions.
- **`useRouter().push()` or `replace()`:** Programmatic navigation from a Client Component, such as after form submission.
- **`redirect()`:** Redirects from a suitable Server Component, Server Action, or Route Handler.

### 14. How are metadata and SEO handled in Next.js?

In the App Router:

- **`metadata`:** Defines static metadata in `layout.tsx` or `page.tsx`.
- **`generateMetadata`:** Produces dynamic metadata from params or fetched data.
- **File conventions:** `favicon.ico`, `opengraph-image`, `twitter-image`, `robots.txt`, and `sitemap.xml`.

Next.js creates the related head tags. SEO still depends on useful content, semantic HTML, canonical URLs, performance, and accessibility.

### 15. Does Next.js support TypeScript?

Yes. `create-next-app` can initialize a TypeScript project, install the required types, and create initial configuration. Next.js supports `.ts` and `.tsx` files, page/layout/route types, and type checking during development or builds.

### 16. Which platforms can deploy a Next.js project?

- **Vercel:** Direct Next.js and Git integration.
- **Node.js server:** Runs with `next build` and `next start`.
- **Docker/container:** Packages the application for cloud or private infrastructure.
- **Cloud platforms with a compatible adapter/runtime:** Examples include AWS, Google Cloud, Azure, Netlify, or Cloudflare, depending on features and adapters.
- **Static hosting:** Works for static export, but does not provide every server-dependent feature.

The deployment platform must support the project's requirements, such as SSR, ISR, Route Handlers, image optimization, or Proxy/Middleware.

## Landing page

[https://portfolio-nganne2203s-projects.vercel.app/](https://portfolio-nganne2203s-projects.vercel.app/)
