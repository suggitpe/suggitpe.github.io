# Specification: Adopt Deep Midnight Slate Glassmorphic UX

## Track Overview
- **Track ID**: `glassmorphic_ux_20260810`
- **Type**: Feature / UI Redesign
- **Status**: New

## Description
Redesign `suggitpe.github.io` using a Deep Midnight Slate Glassmorphic aesthetic. This includes updating site styles, Jekyll layouts (`_layouts/default.html`, `_layouts/page.html`, `_layouts/post.html`), navigation includes (`_includes/sidebar.html`, `_includes/head.html`), and page content (`index.md`, `blog.md`, `presenting.md`, `recipes.md`, `about.md`).

## Core Requirements & Features
1. **Design System & Stylesheet (`public/css/glassmorphic.css`)**:
   - Deep midnight slate canvas background (`#0f172a` / `#0b0f19`).
   - Ambient blurred gradient mesh background orbs (`filter: blur(90px)`).
   - Translucent glass containers (`background: rgba(30, 41, 59, 0.65)`, `backdrop-filter: blur(20px)`).
   - Top-inset border highlights, hover card elevation (`transform: translateY(-3px)`), and arrow transitions.
   - Google Fonts typography (**Plus Jakarta Sans**, **Inter**, **JetBrains Mono**).
   - Translucent tag badges for dates, tags, events, and recipes.

2. **Responsive Dual Device Layout (Laptop & Phone)**:
   - Floating glass sidebar on desktop laptop viewports with avatar badge (`PS`), title, bio, and active pill navigation.
   - Mobile-friendly responsive header layout for phone touchscreens.

3. **Layout & Include Updates**:
   - `_includes/head.html`: Load Google Fonts and `glassmorphic.css`.
   - `_includes/sidebar.html`: Render frosted glass sidebar / mobile navigation with correct `/presenting/` path.
   - `_layouts/default.html`: Wrap pages with ambient mesh canvas and site wrapper.
   - `_layouts/page.html` & `_layouts/post.html`: Structured layouts with glass reader containers and back actions.

4. **Page Content Redesigns**:
   - `index.md`: Hero banner, latest blog cards, talk cards, featured recipe grids.
   - `blog.md`: Filterable glass card list with dates and tag badges.
   - `presenting.md`: Talk cards with event location and date pills.
   - `recipes.md`: Categorized culinary grids with custom icons.
   - `about.md`: Personal bio card and site tech stack badges.

5. **Automated Verification & Human-in-the-Loop Approval**:
   - Automated Liquid syntax verification script before review.
   - All file changes and diffs must be presented to the user for explicit approval prior to committing.

## Acceptance Criteria
- [ ] Site builds cleanly on GitHub Pages with Jekyll.
- [ ] All Liquid syntax tags are balanced and clean.
- [ ] Responsive layout looks stunning on both laptop and mobile phone viewports.
- [ ] Automated verification script confirms Liquid syntax and layout integrity.
- [ ] Working tree clean after human-in-the-loop approved commits.
