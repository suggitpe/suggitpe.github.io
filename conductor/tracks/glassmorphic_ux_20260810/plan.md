# Implementation Plan: Adopt Deep Midnight Slate Glassmorphic UX

## Phase 1: Design System & Core Layout Scaffolding
- [ ] Task: Create `public/css/glassmorphic.css` stylesheet with Deep Midnight Slate glass tokens, ambient mesh animations, typography, and card components
- [ ] Task: Update `_includes/head.html` to link Google Fonts and `glassmorphic.css`
- [ ] Task: Update `_includes/sidebar.html` with avatar badge, icons, active nav state, and fixed `/presenting/` link
- [ ] Task: Update `_layouts/default.html` with ambient background mesh orbs and `.site-wrapper` structure
- [ ] Task: Create `_layouts/page.html` and `_layouts/post.html` glass article templates
- [ ] Task: Phase Verification & Checkpoint (Refer to workflow.md)

## Phase 2: Page Content Redesigns
- [ ] Task: Update `index.md` with glass hero banner, blog cards, talk cards, and recipe grid
- [ ] Task: Update `blog.md` with glass post card list layout
- [ ] Task: Update `presenting.md` with talk cards and event badges
- [ ] Task: Update `recipes.md` with categorized culinary grids and icons
- [ ] Task: Update `about.md` with bio profile card and tech stack badges
- [ ] Task: Phase Verification & Checkpoint (Refer to workflow.md)

## Phase 3: Automated Verification & Human Review
- [ ] Task: Run automated Liquid syntax & link verification script across all updated files
- [ ] Task: Present change set diff and proposed commit message for Human-in-the-Loop review & approval
- [ ] Task: Execute git commit and push upon explicit user confirmation
- [ ] Task: Phase Verification & Checkpoint (Refer to workflow.md)
