# Carousel Skill Update Design

## Objective

Update the existing `carousel-for-ig` skill in `trinhtphat/carousel` so it can be reused and revised frequently across brands, topics, products, and languages. The skill must retain the proven F&B editorial workflow while removing any dependency on The Botanist or one specific campaign.

## Scope

The update covers the complete path from a raw topic to a saved, editable Canva carousel:

1. Clarify audience, learning outcome, objective, brand role, language, slide count, and approval owner.
2. Research current signals and local context when the topic needs evidence.
3. Select an editorial angle that is useful, visually viable, and distinct from recent content.
4. Create a slide-by-slide narrative before visual production.
5. Define a project-specific visual system instead of applying one permanent brand look.
6. Generate or source image assets with consistent lighting, framing, and negative space.
7. Build editable typography and layout in Canva.
8. Review mobile readability, slide order, brand restraint, spelling, and asset integrity.
9. Save only after the user reviews the preview and explicitly approves it.
10. Package approved assets and record lessons for the next update.

## Generalisation Rules

- Keep the skill name `carousel-for-ig` and repository name `carousel`.
- Do not put The Botanist or any other brand name in the skill name, description, UI metadata, or required workflow.
- Treat brand palettes, typography, packshots, product claims, glassware, local ingredients, language, and recipes as project inputs.
- Preserve culturally specific ingredient or product names when the user requests it, even when the rest of the copy changes language.
- Keep current cocktail and F&B knowledge as examples and references, not universal defaults.

## Proposed Repository Changes

### `SKILL.md`

Shorten the entry point and make it route to specialised references. Add the production decisions that materially change outcomes:

- Decide whether images should contain typography. Default to clean image backgrounds and editable Canva typography.
- Confirm product integration and distinguish an authentic supplied packshot from AI-generated scene imagery.
- Require a mobile-size preview before saving.
- Preserve approved slides and revise only the requested scope.
- Record explicit approval before committing Canva draft changes or publishing.

### `references/production-workflow.md`

Extend the workflow with:

- Project variable sheet for brand, language, glassware, ingredients, product presence, palette, type hierarchy, and slide count.
- Image production sequence: style selection, prompt matrix, generation, visual consistency review, and Canva placement.
- Copy language conversion that preserves approved proper nouns and local terms.
- Recipe handling that treats user-supplied wording as authoritative.

### `references/canva-production.md`

Add a focused Canva guide covering:

- Work from a 1080 × 1350 px editable design.
- Keep photography and typography separate unless the user explicitly requests baked-in text.
- Use transactions for element edits, preview every affected page, obtain approval, then commit.
- Handle expired transactions by reopening the saved design and reapplying only unsaved changes.
- Verify narrative page order after moving pages.
- Judge typography from rendered thumbnails at mobile scale; do not trust numeric font sizes alone.
- Prefer shorter copy or a wider existing text container when Canva text boxes resist resizing.

### `references/visual-asset-workflow.md`

Add guidance for image generation and sourcing:

- Use a declared visual style consistently across the carousel.
- Generate clean backgrounds with subject integrity and negative space.
- Honour user-specified glassware, ingredients, props, and local context.
- Never generate an imitation branded bottle or alter a supplied packshot.
- Place authentic product visuals only where the narrative earns brand presence.

### `references/carousel-trending-2026.html` and `references/design-system-2026.md`

Use the user-supplied `Carousel Trending 2026.html` as the canonical colour and typography source for the skill:

- Preserve the supplied HTML in the repository as an auditable source snapshot.
- Extract a concise Markdown reference that the skill reads when deciding colour and typography.
- Use the three defined typography roles: DM Serif Display for editorial display, Hanken Grotesk for body and heavy impact, and IBM Plex Mono for labels, numbering, and data.
- Preserve the 1080 px type scale: hook 80–96 px, hook subtitle 36 px, body title 48–64 px, body copy 32–36 px, label or slide number 24 px, and CTA headline 72 px.
- Apply the source rule that copy below 32 px should be shortened instead of reduced further.
- Route palette choice through three project lanes:
  - Warm Editorial: `#F0EEE9`, `#A47864`, `#6B7B3F`, `#C9B79C`, `#3D2C40`.
  - High Contrast: `#0E7C7B`, `#F76C5E`, `#F9F7F3`, `#2B2B2B`, `#C6F06B`.
  - Cool Authority: `#DCE7F2`, `#A9C6E8`, `#5A8FC7`, `#2E5E8C`, `#16324F`.
- Treat these lanes as decision standards, not as one mandatory palette for every brand. Approved brand assets and explicit user choices override the default lane.
- Use the same design tokens to improve the README visual hierarchy without copying the interactive page implementation.

### `references/qa-checklist.md`

Add checks for:

- Readability at phone-size preview.
- Broken or literal newline markers.
- Text boxes that wrap into one-word columns.
- Page numbers and closing-slide order.
- Exact recipe and product wording.
- Consistent terminology across languages.
- Canva transaction state, preview approval, and saved revision verification.

### `references/case-study-mini-martini-cu-kieu.md`

Capture the reusable lessons from the completed project without turning its brand choices into global defaults:

- Nick & Nora glassware was an explicit project constraint.
- Củ Kiệu remained untranslated while surrounding copy changed to English.
- Soft branding worked through one product-relevant recipe slide.
- Generated imagery excluded the bottle; authentic product imagery remains the correct source for branded packaging.
- English copy required a second typography pass because translated text changed line length.
- Canva text containers sometimes ignored width changes, so concise copy and container reassignment were needed.
- The closing slide had to be moved after the content slides and then verified.

### `README.md` and showcase assets

Turn the README into a visual landing page for the skill while keeping the repository generic:

- Add a concise hero section that explains the outcome before the implementation details.
- Add a finished-output gallery using selected carousel slides from the Mini Martini × Củ Kiệu case study.
- Store stable preview images inside `assets/showcase/`; do not embed temporary Canva export URLs.
- Use a cover, a content or recipe slide, and a closing slide to demonstrate narrative range.
- Add short captions that explain what each visual demonstrates: hook, editable editorial hierarchy, and closing CTA.
- Keep The Botanist and Củ Kiệu references inside the labelled case-study area, not in the skill name or trigger description.
- Add a compact workflow diagram and a clear repository map below the showcase.
- Verify every embedded image path and render the README locally before deployment.

### `tests/scenarios.md`

Add realistic behavioural scenarios and expected decisions for:

- A brand requests subtle presence without advertising tone.
- A user changes the glassware after approving the concept.
- The carousel changes language but must preserve a local ingredient name.
- A recipe must match user-supplied wording exactly.
- Typography looks small or wraps badly in Canva.
- A Canva editing transaction expires before commit.
- A closing slide is generated in the wrong order.

## Validation

1. Run a baseline package test before changing the skill and record which new requirements are absent.
2. Update the skill and references.
3. Run the same package test and require all invariants to pass.
4. Run the official skill `quick_validate.py` validator.
5. Review the rendered Markdown, links, YAML metadata, and Git diff.
6. Confirm no file contains brand-specific trigger language.
7. Confirm the README gallery uses stable repository assets and renders without broken images.
8. Confirm the extracted design-system reference matches the supplied HTML tokens and type scale.
9. Commit and push to `trinhtphat/carousel` on `main` after validation.

## Success Criteria

- The skill is discoverable for Instagram carousel work without mentioning a particular brand in its trigger.
- A future project can supply a different brand, product, language, glass, ingredient, palette, and recipe without editing the core skill.
- Canva drafts remain editable and require rendered preview approval before saving.
- The workflow detects the concrete failures observed in the Mini Martini × Củ Kiệu project.
- The README presents polished finished visuals without making the skill brand-specific.
- Colour and typography decisions trace back to the supplied Carousel Trending 2026 reference.
- The repository passes structural validation and the update is committed and pushed to GitHub.
