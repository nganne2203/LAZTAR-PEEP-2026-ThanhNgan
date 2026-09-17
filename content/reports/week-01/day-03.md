+++
title = "Day 03 - 17/09/2026 (Remote)"
weight = 3
+++

# Daily Report - Day 03

**Work mode:** Remote
**Project:** StudyFlow AI landing page

## A. Practical work

### 1. Objective

Today I worked remotely on the StudyFlow AI landing page. StudyFlow AI is a fictional AI-powered study assistant that helps students understand difficult concepts, summarize notes, practice with quizzes, plan study sessions, and follow their progress. My goal was to turn this product idea into a responsive, interactive frontend that could be presented as a portfolio project.

### 2. Product definition and UI/UX planning

- Defined the product name, tagline, target users, problems, value proposition, features, and calls to action before coding.
- Planned the page flow from the hero and product explanation through the interactive demo, dashboard preview, pricing, FAQ, and final call to action.
- Created detailed desktop and mobile text wireframes, a design system, responsive rules, accessibility requirements, and an implementation plan in the project documentation.
- Chose a calm SaaS visual style with clear typography, generous spacing, rounded cards, subtle borders, and a restrained purple accent. Product interface previews carry the visual story without stock images.

### 3. Landing page implementation

- Built the page with Next.js App Router, React, TypeScript, Tailwind CSS, Motion, and Lucide icons. The existing project already used Next.js, so I kept it as the application framework instead of adding Vite or React Router.
- Organized the page into reusable layout, section, and UI components. Kept feature descriptions, pricing plans, testimonials, FAQ answers, and sample prompts in typed local data.
- Implemented the navigation, hero conversation preview, study-topic strip, problem section, six feature cards, three-step workflow, dashboard preview, sample statistics, three fictional testimonials, three pricing plans, FAQ, final call to action, and footer.
- Built a frontend-only AI demo with suggested prompts and a custom question field. It shows loading and typing states, scripted answers, follow-up actions, and a reset control. No request is sent to an AI service.
- Added a mobile menu and responsive layouts for the hero, cards, demo, dashboard, pricing, and footer. Added semantic headings, keyboard-accessible controls, visible focus styles, FAQ state, screen-reader status, and reduced-motion support.
- Clearly labeled metrics, student stories, pricing, and dashboard figures as illustrative demo content.

### 4. Verification and issues resolved

- Ran ESLint, TypeScript type checking, and a production build successfully.
- Checked the page in a browser at desktop and mobile widths. Tested the navigation menu, suggested and custom demo prompts, reset action, FAQ accordion, and horizontal overflow at a 390px viewport.
- Adjusted the desktop hero headline so it no longer crowded the product preview and fixed a call-to-action arrow that wrapped onto a new line on mobile.
- The initial build depended on fetching a web font and Turbopack could not start a worker in the restricted environment. I switched to a local system font stack and configured the production build to use webpack.

## B. Summary

### What I learned

- A product definition and wireframe make the implementation more consistent and reduce guesswork while building sections.
- Next.js Server Components are useful for static landing-page content, while the interactive demo, mobile menu, FAQ, and animations need Client Components.
- Small interactions make a landing page feel more like a real product, but a demo must clearly explain when answers and product data are simulated.
- Responsive design requires checking the actual layout and controls at narrow widths, not only shrinking desktop columns.

### Challenges and how I addressed them

- **Balancing a strong hero with a readable product preview:** I adjusted the headline size, spacing, and floating card position after reviewing the desktop rendering.
- **Maintaining usability on mobile:** I stacked the layout, gave the dashboard a compact navigation strip, checked that controls remained usable, and verified there was no horizontal page overflow.
- **Keeping the AI preview honest:** I used local scripted responses, added a transparent fallback for unsupported topics, and stated that the demo does not upload or store study material.

## URL PAGE

- Project repository: [StudyFlowAI on GitHub](https://github.com/nganne2203/StudyFlowAI)
- Public preview: [StudyFlowAI on Vercel](https://studyflowai-eta.vercel.app)
