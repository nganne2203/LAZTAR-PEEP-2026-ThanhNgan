
+++
title = "Day 03 - 17/09/2026 (Remote)"
weight = 3
+++

# Daily Report - Day 03

* **Work format:** Remote
* **Project:** StudyFlow AI landing page

## A. Practical work

### 1. Objective

Today I worked remotely and built the landing page for StudyFlow AI. This is an idea for an AI-powered learning assistant that helps students understand difficult concepts, summarize documents, practice with questions, create study plans, and track progress. My goal was to turn the product idea into an interactive front-end interface that works well across devices and is suitable for a portfolio.

### 2. Product definition and UI/UX planning

- Define the product name, tagline, target user group, problem to solve, core value, features, and call to action before writing the interface.
- Arrange the content flow from the hero and product introduction to the interactive demo, dashboard preview, pricing table, FAQ, and final call to action.
- Create text-based wireframes for desktop and mobile, a design system, responsive rules, accessibility requirements, and implementation plans in the project documentation.
- Choose a modern SaaS style with clean typography, generous spacing, rounded cards, subtle borders, and purple as the main accent color. Product preview mockups are the visual focus of the page.

### 3. Landing page implementation

- Build the page using Next.js App Router, React, TypeScript, Tailwind CSS, Motion, and Lucide icons. Since the current project already uses Next.js, I continued with this framework instead of adding Vite or React Router.
- Split the interface into reusable components for layout, sections, and shared UI elements. Data for features, pricing, testimonials, FAQ, and sample questions is managed separately with clear TypeScript types.
- Complete the navigation bar, conversation-style hero section, learning topic strip, problem statement section, six feature cards, three-step process, dashboard preview, sample statistics, three fictional testimonials, three pricing plans, FAQ, final call to action, and footer.
- Create a fully front-end AI demo: choose a suggested question or enter your own, show loading states and typing effects, receive sample responses, select the next question, and reset the conversation. The demo does not call a real AI service.
- Design the mobile menu and responsive layout for the hero, cards, demo, dashboard, pricing section, and footer. Add a proper heading structure, keyboard controls, clear focus states, FAQ states for screen readers, and reduced-motion support.
- Clarify that the numbers, student stories, pricing, and dashboard data are illustrative only.

### 4. Testing and issue handling

- Run ESLint, check TypeScript types, and confirm the production build succeeds.
- Test the page in desktop and mobile browser sizes. Try the menu, suggested questions, custom questions, demo reset, FAQ, and verify there is no horizontal overflow on a 390px-wide screen.
- Adjust the hero heading size so it does not overlap the product preview; fix the action button arrow icon wrapping on mobile.
- The first build depended on loading fonts from the network, and Turbopack could not start workers in the restricted environment. I switched to the system font stack and configured the production build to use webpack.

## B. Summary

### What I learned

- Defining the product and sketching the wireframe beforehand makes the interface more consistent and reduces impulsive decisions during implementation.
- Next.js Server Components are suitable for static landing page content; the interactive demo, mobile menu, FAQ, and animations require Client Components.
- Small interactions make the landing page communicate the product more clearly, but the simulated responses and data must be labeled transparently.
- Responsive design needs to be tested on real screens or narrow viewports, not only by shrinking the desktop layout.

### Challenges and solutions

- **Balancing a prominent hero section with a readable product preview:** I tested the desktop layout first and then adjusted font sizes, spacing, and floating card positioning.
- **Keeping the mobile experience smooth:** I stacked columns, simplified the dashboard navigation, checked button behavior, and confirmed the page had no horizontal overflow.
- **Presenting the AI demo accurately:** I used local sample responses, clearly communicated the limitation around unsupported topics, and stated that the demo does not upload or save study materials.

## URL PAGE

- Project repository: [StudyFlowAI on GitHub](https://github.com/nganne2203/StudyFlowAI)
- Public preview: [StudyFlowAI on Vercel](https://studyflowai-eta.vercel.app)
