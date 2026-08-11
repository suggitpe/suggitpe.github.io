# Project Workflow: Pete Suggitt Personal Site (`suggitpe.github.io`)

## Core Operating Principles

1. **The Plan is the Source of Truth:** All features, bug fixes, and refactoring tasks must be tracked in `conductor/tracks/<track_id>/plan.md`.
2. **Preview-First Proposal Protocol (MANDATORY):** Before making any actual modifications to the site's layout, templates, CSS, or structure, the agent MUST create a standalone preview page (`preview.html` or browser artifact preview) for the user to review. No core site files are updated until the proposal preview is explicitly approved by the user.
3. **Human-in-the-Loop Pre-Commit Approval (MANDATORY):** The agent MUST NOT execute any `git commit` or push actions automatically. Every change set, file diff, and proposed commit message MUST be presented to the user for explicit review and confirmation before any git commit operation is performed.
4. **Dual Device Responsiveness (Laptop & Mobile Phone):** All proposals and previews must account for users on laptops (wide viewport, hover interactions, multi-column grids) and mobile phones (narrow viewport, touch targets, vertical stacking).
5. **Specification-Driven Development:** Changes must conform to `product.md`, `product-guidelines.md`, `tech-stack.md`, and code style guides.
6. **Build & Markup Integrity:** Verify Liquid syntax tag symmetry, HTML semantics, and relative URL references before completing any task.

---

## Proposal & Task Lifecycle

### Phase 1: Preview Proposal (Mandatory Pre-Commit Step)
1. **Analyze Task**: Read task requirements from active track `plan.md`.
2. **Draft Preview Page**: Create a standalone HTML preview file (`preview.html` in project root or browser artifact) showcasing the proposed UI/UX, styling, or structural changes.
3. **Verify Dual Device Layout**: Ensure `preview.html` is responsive for both laptop screens and mobile phones.
4. **Present Preview to User**: Provide clickable link to `preview.html` or local HTTP preview server URL.
5. **Await User Feedback**:
   - **If Approved**: Proceed to Phase 2 (Implementation).
   - **If Revisions Requested**: Update `preview.html` and re-submit proposal until approved.
   - **If Rejected**: Revert preview draft without modifying production site files.

### Phase 2: Implementation & Human Review
1. **Mark Task In Progress**: Edit `plan.md` to change `[ ]` to `[~]`.
2. **Apply Code/File Changes**: Modify target Jekyll files (`_includes/`, `_layouts/`, `_posts/`, `public/css/`, `.md` pages).
3. **Validate Syntax & Links**: Verify Liquid tag balance ({% raw %}`{% %}` and `{{ }}`{% endraw %}), valid HTML markup, and local file links.

4. **Present Change Set for Human Review**: Present a diff summary, changed file list, and proposed commit message to the user for explicit approval.
5. **Human-in-the-Loop Confirmation**: Wait for explicit user confirmation before running `git commit`.
6. **Commit Changes**: Upon explicit confirmation, perform the commit with conventional syntax.
7. **Mark Task Complete**: Update `plan.md` from `[~]` to `[x]` with commit hash SHA.

---

## Quality Gates & Verification Checklist

Before requesting human-in-the-loop commit approval or marking any task complete in `plan.md`, verify:
- [ ] Preview proposal was reviewed and approved by user
- [ ] Laptop & Mobile Phone responsiveness verified
- [ ] All Liquid syntax tags are balanced and clean
- [ ] HTML markup is semantic and valid
- [ ] No broken relative links or missing assets
- [ ] Change set diff and proposed commit message reviewed by user prior to commit
- [ ] Git commit message follows conventional guidelines

---

## Git Commit Guidelines

Format: `<type>(<scope>): <description>`

Examples:
- `feat(ui): Add dark glassmorphic hero banner preview`
- `fix(nav): Correct presenting link in sidebar`
- `docs(conductor): Initialize spec-driven development documentation`
