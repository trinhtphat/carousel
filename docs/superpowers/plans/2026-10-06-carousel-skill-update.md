# Carousel Skill Update Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Upgrade the existing generic Instagram carousel skill, add Canva production guidance and a polished README showcase, then validate, commit, and push the result to `trinhtphat/carousel`.

**Architecture:** Keep `SKILL.md` as the concise router and move conditional production detail into focused references. Use one dependency-free Python validator to test package invariants and stable local PNG assets for the README gallery.

**Tech Stack:** Markdown, YAML, Python standard library, Git, GitHub, Canva export assets.

**Spec:** `docs/superpowers/specs/2026-10-06-carousel-skill-update-design.md`

## Global Constraints

- Keep the skill name `carousel-for-ig` and repository name `carousel`.
- Do not place The Botanist or another brand name in the skill name, trigger description, or UI metadata.
- Treat brand, product, language, glassware, ingredient, palette, typography, recipe, and slide count as project inputs.
- Keep Canva typography editable by default and require rendered preview approval before saving.
- Use only stable repository assets in the README; do not embed temporary Canva export URLs.
- Preserve culturally specific ingredient or product names when the user requests it.

## Review Focus

- Missing or expired Canva asset URLs must not leave broken README images; the validator checks only local `assets/showcase/*.png` paths.
- Brand-specific case-study language must not leak into automatic skill discovery; tests inspect frontmatter and UI metadata.
- A language change must preserve approved local terms and exact user-supplied recipe copy; scenario coverage names this behavior.
- Canva transaction expiry and wrong page order must have explicit recovery and verification guidance.
- Typography must be judged from rendered phone-size previews, including literal newline markers and one-word columns.

---

### Task 1: Add a failing package validation test

**Files:**
- Create: `tests/validate_skill_package.py`

**Interfaces:**
- Consumes: repository root files and directories.
- Produces: process exit code `0` only when the required references, README assets, generic metadata, and PNG invariants pass.

- [ ] **Step 1: Write the failing validator**

Add tests named `test_required_files`, `test_generic_discovery_metadata`, `test_skill_routes_to_new_references`, `test_readme_uses_stable_showcase_assets`, and `test_showcase_pngs_are_valid`.

- [ ] **Step 2: Run the validator to verify baseline failure**

Run: `python tests/validate_skill_package.py`

Expected: FAIL because the new references and showcase assets do not exist and README does not contain the gallery.

- [ ] **Step 3: Commit the failing test**

Run:

```bash
git add tests/validate_skill_package.py
git commit -m "test: define carousel skill package invariants"
```

### Task 2: Update the skill router and production references

**Files:**
- Modify: `SKILL.md`
- Modify: `references/production-workflow.md`
- Modify: `references/qa-checklist.md`
- Create: `references/canva-production.md`
- Create: `references/visual-asset-workflow.md`
- Create: `references/case-study-mini-martini-cu-kieu.md`
- Create: `tests/scenarios.md`

**Interfaces:**
- Consumes: the approved design spec and existing production workflow.
- Produces: a generic routing skill plus focused production, Canva, visual-asset, case-study, and behavioral-test references.

- [ ] **Step 1: Update `SKILL.md`**

Keep the entry point concise, route full production work to the new references, and add the image-versus-typography, authentic-packshot, mobile-preview, scoped-revision, and approval decisions.

- [ ] **Step 2: Extend production and QA references**

Add project variables, prompt-matrix guidance, language-preservation rules, exact recipe handling, phone-size readability, page-order verification, and transaction-state checks.

- [ ] **Step 3: Add focused Canva and visual-asset references**

Document editable Canva layers, transaction recovery, rendered-preview review, consistent image generation, negative space, authentic branded packaging, and story-earned brand presence.

- [ ] **Step 4: Add the Mini Martini × Củ Kiệu case study and scenarios**

Record reusable decisions without adding brand-specific triggers. Include expected behavior for glassware changes, language preservation, exact recipes, small typography, expired transactions, and wrong page order.

- [ ] **Step 5: Run the validator**

Run: `python tests/validate_skill_package.py`

Expected: still FAIL only for README showcase requirements.

- [ ] **Step 6: Commit the workflow update**

Run:

```bash
git add SKILL.md references tests/scenarios.md
git commit -m "feat: generalize editable carousel production workflow"
```

### Task 3: Download and verify Canva showcase assets

**Files:**
- Create: `assets/showcase/01-cover.png`
- Create: `assets/showcase/05-recipe.png`
- Create: `assets/showcase/07-closing.png`

**Interfaces:**
- Consumes: approved Canva design `DAHXN9SZ5uw`, pages 1, 5, and 7.
- Produces: three stable PNG files stored in the repository.

- [ ] **Step 1: Export or download the approved Canva pages**

Use Canva export/download capability for pages 1, 5, and 7. Do not use temporary URLs in committed Markdown.

- [ ] **Step 2: Verify each image**

Check PNG signature, decoded dimensions, portrait orientation, expected slide content, and nonzero file size.

- [ ] **Step 3: Commit the showcase assets**

Run:

```bash
git add assets/showcase
git commit -m "assets: add finished carousel showcase"
```

### Task 4: Redesign README as a visual skill landing page

**Files:**
- Modify: `README.md`

**Interfaces:**
- Consumes: the updated skill workflow and `assets/showcase/*.png`.
- Produces: a GitHub-renderable README with a hero, finished-output gallery, workflow, safeguards, repository map, and example invocation.

- [ ] **Step 1: Add the hero and outcome summary**

Lead with the reusable result and clarify that brands, ingredients, languages, and recipes are project inputs.

- [ ] **Step 2: Add the finished-output gallery**

Embed the three local showcase images in a GitHub-compatible table and caption them as hook, recipe hierarchy, and closing CTA examples.

- [ ] **Step 3: Refresh workflow and repository sections**

Link the new references, keep the Mermaid workflow compact, and remove any wording that presents one cocktail visual system as the universal default.

- [ ] **Step 4: Run the package validator**

Run: `python tests/validate_skill_package.py`

Expected: PASS.

- [ ] **Step 5: Commit the README update**

Run:

```bash
git add README.md
git commit -m "docs: add visual carousel showcase"
```

### Task 5: Validate the complete skill and deploy

**Files:**
- Verify: all changed files.

**Interfaces:**
- Consumes: completed repository state.
- Produces: validated commits on `main` pushed to `trinhtphat/carousel`.

- [ ] **Step 1: Run all package tests**

Run: `python tests/validate_skill_package.py`

Expected: PASS with every invariant listed.

- [ ] **Step 2: Run the official skill validator**

Run: `python C:/Users/Lenovo/.codex/skills/.system/skill-creator/scripts/quick_validate.py .`

Expected: `Skill is valid!`

- [ ] **Step 3: Inspect final diff and repository state**

Run: `git status --short`, `git diff HEAD~4..HEAD --check`, and `git log --oneline -8`.

Expected: clean worktree, no whitespace errors, and the expected commits.

- [ ] **Step 4: Push the validated branch**

Run: `git push origin main`

Expected: remote `main` advances to the final local commit.

- [ ] **Step 5: Verify GitHub**

Fetch the remote README, SKILL.md, new references, and final commit SHA. Confirm the gallery paths resolve and the repository page is available at `https://github.com/trinhtphat/carousel`.
