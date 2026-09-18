+++
title = "Day 04 - 18/09/2026 (Remote)"
weight = 3
+++

# Daily Report - Day 04

- **Work mode:** Remote
- **Project:** StudyFlow AI landing page

## A. Practical work

### 1. Objective

Today I refactored the StudyFlow AI landing page and added a Vietnamese version. The goal was to let visitors switch between English and Vietnamese while keeping one maintainable set of UI components. English remains the default language.

### 2. Refactoring the source code

- Moved page composition into a shared LandingPage component. Both language routes now render the same sections instead of maintaining two separate page implementations.
- Created a typed localization module with English and Vietnamese copy. The Locale and SiteCopy types make the expected content structure explicit in TypeScript.
- Updated the navbar, hero, problem section, six feature cards, interactive demo, three-step workflow, dashboard preview, statistics, testimonials, pricing, FAQ, final call to action, and footer to receive localized copy through props.
- Moved interface labels, descriptive text, sample data, suggested prompts, FAQ answers, and scripted demo responses into the language data. This keeps presentation logic separate from content and makes later copy changes easier.
- Preserved the frontend-only nature of the product preview. The AI answers, metrics, testimonials, and prices are still demo data; no backend or real AI API was added.

### 3. Vietnamese version and language switch

- Kept the English landing page at the root URL and added the Vietnamese page at /vi.
- Added an EN/VI switch in the navbar. It marks the current language and remains available in the responsive header.
- Set the HTML language and page metadata separately for each route, with alternate-language URLs for search engines.
- Translated the landing-page content, dashboard labels, pricing, FAQ, and interactive demo. The demo recognizes relevant Vietnamese prompt keywords and returns Vietnamese sample answers.
- Adjusted typography spacing and navigation behavior for longer Vietnamese text and smaller screens.

### 4. Verification

- ESLint completed without errors.
- The production build and TypeScript check completed successfully.
- The build generated both static routes: / for English and /vi for Vietnamese.

## B. Summary

### What I learned

- Keeping translations in one typed module makes a multilingual interface easier to review and maintain.
- A shared component tree prevents the English and Vietnamese pages from drifting apart when the layout changes.
- Localization includes more than visible headings: form labels, accessibility text, metadata, mock responses, and responsive spacing also need attention.

### Challenges and how I addressed them

- **Hard-coded English text across many components:** I replaced it with localized props and reused one LandingPage composition for both routes.
- **Longer Vietnamese copy in the existing layout:** I adjusted heading letter spacing and the navigation breakpoint so the language switch and menu fit more reliably.
- **Demo responses tied to English keywords:** I added Vietnamese prompt matching and localized sample answers while keeping the behavior entirely in the browser.

## URL PAGE

- Project repository: [StudyFlowAI on GitHub](https://github.com/nganne2203/StudyFlowAI)
- Public preview: [StudyFlowAI on Vercel](https://studyflowai-eta.vercel.app)
